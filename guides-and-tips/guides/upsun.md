---
description: >-
  Give every Upsun preview environment its own Mailtrap Email Sandbox with an
  Upsun activity script, so preview environments catch emails instead of
  sending them.
---

# Upsun

Give every [Upsun](https://upsun.com/) preview environment its own [Email Sandbox](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/getting-started/email-sandbox), so the emails your pull request and branch environments send are caught instead of reaching real recipients.

<a href="https://developer.upsun.com/docs/integrations/activity" class="button primary">Upsun activity scripts</a>

### Overview

An Upsun [activity script](https://developer.upsun.com/docs/integrations/activity) runs in Upsun after events in your project. The script in this guide keeps one sandbox for each running preview environment:

* When a pull request environment is created or a branch environment is activated, the script creates a sandbox in a Mailtrap project and sets the environment's `MAILER_DSN` variable to that sandbox's SMTP credentials. Upsun redeploys the environment to apply it.
* When an environment is deactivated, paused, or deleted, for example because its pull request was merged or closed, the script deletes its sandbox.
* The script never changes production, or an environment with a `MAILER_DSN` of its own that the script didn't set, such as a staging environment that sends through a real relay.

Each run compares all the environments of the Upsun project with the sandboxes in the Mailtrap project, so a run that fails or comes late is repaired by the next one.

The environment gets only the sandbox's SMTP credentials, which can deliver into that sandbox and nothing else. The Mailtrap and Upsun API tokens stay in the script's own variables, which your app can't read.

#### Prerequisites

Before we start, you'll need:

* A Mailtrap plan with a free sandbox for each preview environment you run at the same time. The [sandbox limit of your plan](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/billing/plans#email-sandbox-pricing) counts all sandboxes in your organization, not only the ones the script creates.
* A Mailtrap project for these sandboxes and an [API token](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/general/api-tokens) with **Admin** access to that project only. Once the token [expires](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/general/api-tokens#setting-an-expiration-date), the script stops creating sandboxes.
* An Upsun project connected to a [GitHub repository](https://developer.upsun.com/docs/integrations/source/github), and the [Upsun CLI](https://developer.upsun.com/docs/administration/cli).
* An [Upsun API token](https://developer.upsun.com/cli/api-tokens) of a user who can change variables on your preview environments. We tested with a project admin. Upsun recommends a separate machine user for automated tasks.
* An app that reads its SMTP settings from `MAILER_DSN`, such as one using [Symfony Mailer](symfony.md#email-sandbox-for-symfony). For other variables, see [Adapt the script](upsun.md#adapt-the-script).

### Keep production's settings out of preview environments

{% hint style="danger" %}
Upsun deploys a new preview environment before the script can give it a sandbox. A project variable applies to every environment, and an environment variable is inherited by child environments by default. If production's `MAILER_DSN` is either, a new preview environment can send real emails with production's settings until the script replaces it. Upsun turns off its own email proxy outside production, but ports 465 and 587 to external SMTP servers stay open.
{% endhint %}

Set production's `MAILER_DSN` as an environment variable that other environments don't inherit:

```bash
upsun variable:create --environment main --level environment \
  --name env:MAILER_DSN --value 'YOUR_PRODUCTION_DSN' \
  --inheritable false --sensitive true --visible-build false
```

If production has the variable already, run `upsun variable:update env:MAILER_DSN --environment main --level environment --inheritable false` instead.

Then check that `upsun variable:list --level project` doesn't list `env:MAILER_DSN`. If it does, delete the project variable once production has its own, so that production keeps a value: `upsun variable:delete env:MAILER_DSN --level project`.

### Set up

{% stepper %}
{% step %}
### Create the Mailtrap project and API token

In Mailtrap, create a project for the preview sandboxes, for example "Upsun previews". Then create an [API token](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/general/api-tokens) with **Admin** access to that project and nothing else.

Get the project ID with the new token:

```bash
curl -s -H "Authorization: Bearer YOUR_MAILTRAP_API_TOKEN" https://mailtrap.io/api/projects
```
{% endstep %}

{% step %}
### Add the activity script

Save the script from [The script](upsun.md#the-script) as `mailtrap-sandbox.js` outside your repository. Then, from your Upsun project's folder, add it as an integration:

```bash
upsun integration:add --type script --file ./mailtrap-sandbox.js \
  --events integration.github.fetch,environment.push,environment.branch,environment.activate,environment.deactivate,environment.delete,environment.pause,environment.resume \
  --states complete
```

Note the integration ID in the output. `upsun integration:list` shows it too.

If your repository is on GitLab or Bitbucket, replace `integration.github.fetch` with `integration.gitlab.fetch`, `integration.bitbucket.fetch`, or `integration.bitbucket_server.fetch` from Upsun's [activity reference](https://developer.upsun.com/docs/integrations/activity/reference). We tested the script with GitHub only.
{% endstep %}

{% step %}
### Store the tokens as script variables

Activity script variables are visible only to the script, so your app's environments never see the tokens. The Upsun CLI has no command for them, so add them through the API with `upsun api:curl`:

```bash
PROJECT_ID=YOUR_UPSUN_PROJECT_ID
INTEGRATION_ID=YOUR_INTEGRATION_ID
URL="/projects/$PROJECT_ID/integrations/$INTEGRATION_ID/variables"

upsun api:curl "$URL" -X POST --json '{"name": "MAILTRAP_API_TOKEN", "value": "YOUR_MAILTRAP_API_TOKEN", "is_sensitive": true}'
upsun api:curl "$URL" -X POST --json '{"name": "MAILTRAP_PROJECT_ID", "value": "YOUR_MAILTRAP_PROJECT_ID", "is_sensitive": false}'
upsun api:curl "$URL" -X POST --json '{"name": "UPSUN_API_TOKEN", "value": "YOUR_UPSUN_API_TOKEN", "is_sensitive": true}'
```

Each call returns `"code": 201`. Upsun never shows the value of a sensitive variable again. To keep the tokens out of your shell history, save each JSON body in a file and pass it with `-H 'Content-Type: application/json' -d @body.json` instead of `--json`.
{% endstep %}
{% endstepper %}

### Check that it works

1. Open a pull request. A few seconds later, a sandbox named `upsun-<project ID>-pr-<number>` appears in your Mailtrap project.
2. Check the variable on the new environment:

```bash
upsun variable:get env:MAILER_DSN --environment pr-1
```

3. Once the environment has redeployed, send a test email from it. For a Symfony app:

```bash
upsun ssh --environment pr-1 -- php bin/console mailer:test you@example.com
```

The email appears in the environment's sandbox.

4. Read what the script did:

```bash
upsun integration:activity:list INTEGRATION_ID
upsun integration:activity:log INTEGRATION_ID ACTIVITY_ID
```

A run that created a sandbox logs `Created sandbox upsun-<project ID>-pr-1 (<sandbox ID>)` and `Set env:MAILER_DSN on pr-1 to sandbox <sandbox ID>`.

### What happens on each event

| In your repository or project | What the script does |
| ----------------------------- | -------------------- |
| A pull request is opened | Creates the sandbox and sets `MAILER_DSN` a few seconds after GitHub notifies Upsun, while the environment is still deploying |
| A commit is pushed to the pull request | Nothing: the environment has its sandbox already |
| The pull request is merged or closed | Deletes the sandbox when Upsun deletes the environment |
| A branch is pushed without a pull request | Nothing: Upsun creates the environment inactive |
| An environment is activated | Creates the sandbox and sets `MAILER_DSN` |
| An environment is deactivated or paused | Deletes the sandbox. The environment keeps its `MAILER_DSN` variable, and on activation the script creates a new sandbox and replaces it |
| A commit is pushed to production | Nothing |
| A running environment has a `MAILER_DSN` of its own that the script didn't set | Nothing: it logs `Skipped <environment>: its env:MAILER_DSN was not set by this script`. To hand the environment over to the script, delete its variable |

{% hint style="info" %}
In our tests, Upsun started scripts for `environment.push` on pull request environments up to 30 minutes after the push. The `integration.github.fetch` event comes at once, which is why the script listens to it and checks every environment on each run.
{% endhint %}

### Redeploy cost

Upsun redeploys an environment whenever one of its variables changes. A new pull request environment therefore deploys twice: its first deploy, then a redeploy that applies `MAILER_DSN` and starts right after the first one. Until the redeploy finishes, the environment has no `MAILER_DSN` of its own. On Upsun, Symfony apps use `null://localhost` then, which discards emails.

Later commits to the pull request don't cost an extra deploy, because the script writes the variable only when it's missing. Activating a branch environment, or activating it again after a deactivation, costs one extra deploy.

### Limits and errors

A failed run shows the error in `upsun integration:activity:log`. The script still handles the other environments, and the next run tries again.

| Error | Meaning | What the script does | What you do |
| ----- | ------- | -------------------- | ----------- |
| `422`, "You've reached the sandboxes limit" | Your organization has no free sandbox, or its trial has ended | Sets no `MAILER_DSN` on that environment | Free a sandbox or upgrade your plan, then push again |
| `409`, "Another action in progress" | Another sandbox is being created in your Mailtrap account | Retries up to 5 times | Nothing, or push again if it still fails |
| `429`, "Throttled" | The token went over the [API rate limit](https://app.gitbook.com/s/bUK33X2o81D3048ultKu/rate-limits) | Fails | Push again |
| `401` or `403` | The Mailtrap token has expired or has no Admin access to the project | Fails | Replace the `MAILTRAP_API_TOKEN` script variable |
| `context canceled` | Upsun stopped the run | Nothing more in that run | Nothing: the next run finishes the work |

To replace a script variable, delete it with `upsun api:curl "$URL/MAILTRAP_API_TOKEN" -X DELETE` and add it again.

### Adapt the script

If your app reads its SMTP settings from another variable, change `DSN_VARIABLE`, and change `dsn()` to return the format your framework expects. The sandbox object it receives has `username`, `password`, `domain`, and `smtp_ports`.

The script recognizes the variables it wrote by the `mailtrap_sandbox_id` attribute it stores on them, which Upsun shows even for a sensitive variable. Keep that attribute if you change `writeDsn()`.

### The script

{% code title="mailtrap-sandbox.js" lineNumbers="true" %}
```javascript
// Upsun activity script: gives every running preview environment its own Mailtrap Sandbox.
//
// Each run compares the project's environments with the sandboxes in one Mailtrap project.
// It deletes the sandboxes of environments that are gone or inactive, then creates a sandbox
// and sets MAILER_DSN for each running non-production environment that lacks one.
// It never reads which environment the activity was about: Upsun can run a script many
// minutes after the activity, when that environment may already be gone.
// An environment with a MAILER_DSN of its own that this script didn't write is left alone.
//
// Script variables: MAILTRAP_API_TOKEN, MAILTRAP_PROJECT_ID, UPSUN_API_TOKEN.

var MAILTRAP_API = 'https://mailtrap.io/api';
var UPSUN_API = 'https://api.upsun.com';
var UPSUN_AUTH = 'https://auth.upsun.com/oauth2/token';
var DSN_VARIABLE = 'env:MAILER_DSN';
var SMTP_PORT = 587; // Upsun blocks outbound port 25
var CREATE_ATTEMPTS = 5;
var NAME_PREFIX = 'upsun-' + activity.project + '-';

function call(base, token, method, path, body) {
  var options = { method: method, headers: { Authorization: 'Bearer ' + token } };
  if (body !== undefined) {
    options.headers['Content-Type'] = 'application/json';
    options.body = JSON.stringify(body);
  }
  return fetch(base + path, options);
}

function fail(what, response) {
  throw new Error(what + ' failed with ' + response.status + ': ' + response.text().slice(0, 300));
}

function mailtrap(method, path, body) {
  return call(MAILTRAP_API, variables.MAILTRAP_API_TOKEN, method, path, body);
}

var upsunToken = null;

function upsun(method, path, body) {
  if (!upsunToken) {
    var auth = fetch(UPSUN_AUTH, {
      method: 'POST',
      headers: {
        Authorization: 'Basic cGxhdGZvcm0tYXBpLXVzZXI6', // "platform-api-user:" in base64
        'Content-Type': 'application/x-www-form-urlencoded',
      },
      body: 'grant_type=api_token&api_token=' + encodeURIComponent(variables.UPSUN_API_TOKEN),
    });
    if (!auth.ok) fail('Upsun token exchange', auth);
    upsunToken = auth.json().access_token;
  }
  return call(UPSUN_API, upsunToken, method, '/projects/' + activity.project + path, body);
}

// "dirty" means an activity is in progress: a running environment being redeployed, a new
// pull request environment during its first deploy, but also a new branch that stays inactive.
function isRunning(environment) {
  if (environment.status === 'active') return true;
  return environment.status === 'dirty' && (environment.has_deployment || environment.is_pr);
}

// IDs of the running non-production environments.
function previewEnvironments() {
  var response = upsun('GET', '/environments');
  if (!response.ok) fail('Listing Upsun environments', response);
  return response.json()
    .filter(function (environment) { return environment.type !== 'production' && isRunning(environment); })
    .map(function (environment) { return environment.id; });
}

// This project's sandboxes in the Mailtrap project, by environment id, oldest first.
function sandboxesByEnvironment() {
  var response = mailtrap('GET', '/sandboxes');
  if (!response.ok) fail('Listing Mailtrap sandboxes', response);
  var sandboxes = {};
  response.json().sort(function (a, b) { return a.id - b.id; }).forEach(function (sandbox) {
    if (String(sandbox.project_id) !== String(variables.MAILTRAP_PROJECT_ID)) return;
    if (sandbox.name.indexOf(NAME_PREFIX) !== 0) return;
    var environmentId = sandbox.name.slice(NAME_PREFIX.length);
    (sandboxes[environmentId] = sandboxes[environmentId] || []).push(sandbox);
  });
  return sandboxes;
}

function createSandbox(environmentId) {
  var name = NAME_PREFIX + environmentId;
  if (name.length > 100) throw new Error('Sandbox name longer than 100 characters: ' + name);
  for (var attempt = 1; attempt <= CREATE_ATTEMPTS; attempt++) {
    var response = mailtrap(
      'POST',
      '/projects/' + variables.MAILTRAP_PROJECT_ID + '/sandboxes',
      { sandbox: { name: name } }
    );
    if (response.ok) return response.json();
    // 409: another sandbox is being created in this Mailtrap account. Each one takes Mailtrap
    // about 0.6 seconds to return, so the retries are already spaced out.
    if (response.status !== 409) fail('Creating sandbox ' + name, response); // 422: limit reached
  }
  throw new Error('Creating sandbox ' + name + ': Mailtrap still busy after ' + CREATE_ATTEMPTS + ' attempts');
}

function deleteSandbox(sandbox) {
  var response = mailtrap('DELETE', '/sandboxes/' + sandbox.id);
  if (!response.ok && response.status !== 404) fail('Deleting sandbox ' + sandbox.name, response);
  console.log('Deleted sandbox ' + sandbox.name + ' (' + sandbox.id + ')');
}

function dsn(sandbox) {
  return 'smtp://' + encodeURIComponent(sandbox.username) + ':' +
    encodeURIComponent(sandbox.password) + '@' + sandbox.domain + ':' + SMTP_PORT;
}

function variablesPath(environmentId) {
  return '/environments/' + encodeURIComponent(environmentId) + '/variables';
}

function dsnPath(environmentId) {
  return variablesPath(environmentId) + '/' + encodeURIComponent(DSN_VARIABLE);
}

// The variable this script writes carries the sandbox ID in its attributes, which Upsun
// returns even for a sensitive variable. Returns 'missing', 'inherited', 'foreign' (the
// environment's own, not written by this script), or the sandbox ID this script set.
function dsnState(environmentId) {
  var response = upsun('GET', dsnPath(environmentId));
  if (response.status === 404) return 'missing';
  if (!response.ok) fail('Reading ' + DSN_VARIABLE + ' on ' + environmentId, response);
  var variable = response.json();
  if (variable.inherited) return 'inherited';
  return (variable.attributes || {}).mailtrap_sandbox_id || 'foreign';
}

// Every write redeploys the environment, so this is called only when the value must change.
function writeDsn(environmentId, sandbox, state) {
  var body = {
    value: dsn(sandbox),
    is_sensitive: true,
    is_inheritable: false,
    visible_build: false, // a build-visible variable would also trigger a rebuild
    visible_runtime: true,
    attributes: { mailtrap_sandbox_id: String(sandbox.id) },
  };
  // PATCH also turns an inherited variable into the environment's own.
  var response = state === 'missing'
    ? upsun('POST', variablesPath(environmentId), Object.assign({ name: DSN_VARIABLE }, body))
    : upsun('PATCH', dsnPath(environmentId), body);
  if (!response.ok) fail('Setting ' + DSN_VARIABLE + ' on ' + environmentId, response);
  console.log('Set ' + DSN_VARIABLE + ' on ' + environmentId + ' to sandbox ' + sandbox.id);
}

function reconcile() {
  ['MAILTRAP_API_TOKEN', 'MAILTRAP_PROJECT_ID', 'UPSUN_API_TOKEN'].forEach(function (name) {
    if (!variables[name]) throw new Error('Script variable ' + name + ' is not set');
  });
  var errors = [];
  var managed = {}; // environment ID -> state of its MAILER_DSN
  var unknown = {}; // environments whose MAILER_DSN couldn't be read: change nothing there

  previewEnvironments().forEach(function (environmentId) {
    try {
      var state = dsnState(environmentId);
      if (state === 'foreign') {
        console.log('Skipped ' + environmentId + ': its ' + DSN_VARIABLE + ' was not set by this script');
      } else {
        managed[environmentId] = state;
      }
    } catch (error) {
      unknown[environmentId] = true;
      errors.push(environmentId + ': ' + error.message);
    }
  });
  var sandboxes = sandboxesByEnvironment();

  // Deleting first frees sandbox quota for the environments that need one.
  Object.keys(sandboxes).forEach(function (environmentId) {
    if (unknown[environmentId]) return;
    var keep = environmentId in managed ? 1 : 0;
    sandboxes[environmentId].slice(keep).forEach(function (sandbox) {
      try {
        deleteSandbox(sandbox);
      } catch (error) {
        errors.push(error.message);
      }
    });
  });

  Object.keys(managed).forEach(function (environmentId) {
    try {
      var sandbox = (sandboxes[environmentId] || [])[0];
      if (!sandbox) {
        sandbox = createSandbox(environmentId);
        console.log('Created sandbox ' + sandbox.name + ' (' + sandbox.id + ')');
      }
      var state = managed[environmentId];
      if (state !== String(sandbox.id)) writeDsn(environmentId, sandbox, state);
    } catch (error) {
      errors.push(environmentId + ': ' + error.message);
    }
  });

  if (errors.length > 0) throw new Error(errors.join('\n'));
}

reconcile();
```
{% endcode %}

### Clean up orphaned sandboxes

Each run deletes the sandboxes of environments that are gone, so orphaned sandboxes appear only while the script doesn't run, for example after you remove it or while its token is expired. Each one counts toward your sandbox limit.

This Bash script lists the sandboxes named `upsun-<project ID>-...` that belong to no running environment. It needs `curl`, `jq`, and the Upsun CLI:

{% code title="mailtrap-sandbox-orphans.sh" %}
```bash
#!/bin/bash
# Lists the Mailtrap sandboxes that belong to no running environment of the Upsun project.
# DELETE=1 also deletes them. Needs UPSUN_PROJECT_ID, MAILTRAP_API_TOKEN and an authenticated upsun CLI.
PREFIX="upsun-$UPSUN_PROJECT_ID-"
RUNNING=$(upsun environment:list --project "$UPSUN_PROJECT_ID" --no-inactive --pipe) || exit 1
# Production is always listed: an empty list means the call failed, and deleting would remove every sandbox.
[ -n "$RUNNING" ] || { echo "No environments listed for $UPSUN_PROJECT_ID, stopping." >&2; exit 1; }

curl -s -H "Authorization: Bearer $MAILTRAP_API_TOKEN" https://mailtrap.io/api/sandboxes |
  jq -r --arg prefix "$PREFIX" '.[] | select(.name | startswith($prefix)) | "\(.id) \(.name)"' |
  while read -r id name; do
    if ! grep -qxF "${name#"$PREFIX"}" <<<"$RUNNING"; then
      echo "Orphan: $name ($id)"
      if [ "${DELETE:-0}" = "1" ]; then
        curl -s -o /dev/null -w "  deleted: HTTP %{http_code}\n" -X DELETE \
          -H "Authorization: Bearer $MAILTRAP_API_TOKEN" "https://mailtrap.io/api/sandboxes/$id"
      fi
    fi
  done
```
{% endcode %}

Run it to list the orphans, then with `DELETE=1` to delete them. Deleting a sandbox deletes its emails too.

```bash
export UPSUN_PROJECT_ID=YOUR_UPSUN_PROJECT_ID MAILTRAP_API_TOKEN=YOUR_MAILTRAP_API_TOKEN
bash mailtrap-sandbox-orphans.sh
DELETE=1 bash mailtrap-sandbox-orphans.sh
```

### Remove the integration

Delete the integration, then delete the sandboxes it leaves behind with the script from [Clean up orphaned sandboxes](upsun.md#clean-up-orphaned-sandboxes):

```bash
upsun integration:delete INTEGRATION_ID
```

The preview environments keep their `MAILER_DSN` variables. Remove one with `upsun variable:delete env:MAILER_DSN --environment pr-1 --level environment`.

If you need help with this setup, contact our support team at **support@mailtrap.io**.
