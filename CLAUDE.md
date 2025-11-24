# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a GitBook documentation repository for Mailtrap.io, an email API/SMTP service. The repository contains **three GitBook spaces** synced from GitBook.io in a single repository.

### Content Source and Migration

Content was migrated from help.mailtrap.io (managed by HelpScout), which means:
- Files may contain artifacts from the HelpScout format
- Formatting must be adjusted to match GitBook capabilities
- Content should be reviewed and cleaned up during edits

### GitBook Spaces Structure

The repository is organized into three high-level GitBook spaces (directories):

**1. `api-docs/` - API Docs Space**
- API rate limits and error documentation
- Technical API-related information
- API/SMTP endpoints and integration
- Sandbox API endpoints
- Templates API
- Contacts API endpoints
- Documentation rendered based on imported OpenAPI specs  

**2. `documentation/` - Documentation Space**
- Getting Started / Quickstart guides
- Email API/SMTP features (templates, email logs)
- Email Sandbox functionality
- Email Marketing features
- Account and Permissions (User Management)
- Billing information
- FAQ
- Troubleshooting guides

**3. `guides-and-tips/` - Guides & Tips Space**
- Switching guides (from competitors to Mailtrap)
- DNS setup guides for various providers (AWS Route 53, Cloudflare, GoDaddy, etc.)
- Third-party integrations
- AI integration guides

Each space contains:
- `SUMMARY.md` - GitBook table of contents defining the navigation structure (agreed upon by team)
- `README.md` - Landing page for that space
- Nested markdown files organized by feature/topic
- `.gitbook/assets/` - Shared assets directory (in documentation space)

## GitBook Formatting Requirements

This repository uses GitBook-specific markdown syntax.

### IMPORTANT: Use the gitbook-assistant Skill

**Always use the `gitbook-assistant` skill** located in `.claude/skills/gitbook-assistant/` when working with this repository. The skill provides:
- Comprehensive GitBook formatting rules and validation
- Pre-formatted templates for all GitBook blocks
- Syntax checking and error detection
- Content quality guidelines specific to this repository

### GitBook MCP Integration

GitBook MCP (Model Context Protocol) is available for advanced GitBook operations. See documentation at: https://gitbook.com/docs/~gitbook/mcp

This can be used for:
- Searching GitBook documentation
- Accessing GitBook-specific features
- Advanced content operations

### Critical Formatting Rules

**ALL documentation files MUST follow these rules to prevent GitBook rendering errors:**

1. **Frontmatter for titles** - Use YAML frontmatter with `title` and `description` fields, NOT H1 headers for page titles:
   ```yaml
   ---
   title: Page Title Here
   description: Brief description of the page content
   ---
   ```

2. **Heading hierarchy**:
   - H1 (`#`) for major sections like "Overview" and "Next Steps" (NOT for page titles)
   - H2 (`##`) for subsections and inside steppers
   - H3-H4 for nested subsections

3. **No indentation inside stepper steps** - GitBook creates unwanted code blocks from indented content within `{% step %}` blocks

4. **Always close block tags**:
   - `{% hint %}` → `{% endhint %}`
   - `{% tab %}` → `{% endtab %}`
   - `{% tabs %}` → `{% endtabs %}`
   - `{% step %}` → `{% endstep %}`
   - `{% stepper %}` → `{% endstepper %}`
   - `<details>` → `</details>`

5. **Nesting restrictions**:
   - `{% tabs %}` CANNOT be nested inside `<details>` elements
   - Check `.claude/skills/gitbook-assistant/.SKILL.md` for complete nesting rules

### Common GitBook Blocks

- **Hints/Callouts**: `{% hint style="info|warning|danger|success" %}...{% endhint %}`
- **Tabs**: `{% tabs %}` with `{% tab title="..." %}...{% endtab %}`
- **Code blocks**: `{% code title="..." %}` with triple backticks inside
- **Columns**: `{% columns %}` with `{% column %}`
- **Steppers**: `{% stepper %}` with `{% step %}` (no indentation inside steps!)
- **Expandable**: `{% expand title="..." %}` or HTML `<details>`
- **Embeds**: `{% embed url="..." %}`

For detailed syntax, templates, and validation, refer to:
- `.claude/skills/gitbook-assistant/.SKILL.md` - Comprehensive skill definition
- `.claude/skills/gitbook-assistant/resources/gitbook-format-reference.md` - Full format reference
- `.claude/skills/gitbook-assistant/resources/templates/` - Pre-formatted templates

## Images Formatting
- Images assets are stored in the `.gitbook/assets/` directory inside the relevant space directory
- Gitbook-assistant skill has information about image formatting in the `.claude/skills/gitbook-assistant/resources/gitbook-format-reference.md` file.
- After migration from Helpscout some images were not properly formatted and are not included into asset folders. 
-- Some images still host on Helpscout and it can be detected if an image URL like `https://lh7-us.googleusercontent.com/`
-- Images from Helpscout might be removed from Helpscout in the future so we need to fetch them, reformat them and include into asset folders
-- Reformating should include user-friendly name of image and proper alt text
-- Name shouldn't have spaces or special characters
-- Use image vision to understand the image content and provide a meaningful alt text and name. If image is bigger than Read tool max width (2000 pixels), detect it and resize it to fit before submitting to Read tool for recognition.


## Documentation Structure Patterns

### Content Organization
- Use `SUMMARY.md` to define navigation structure
- Maintain consistent nested folder structure matching SUMMARY.md hierarchy
- Place shared assets in `.gitbook/assets/` directory
- Use Gitbook Page links formatting for internal navigation and cross-linking articles

## Working with This Repository

Since this is a documentation-only repository:
- No build, test, or lint commands
- No package managers or dependencies
- Changes are validated through GitBook's preview/publish system
- Focus on markdown syntax correctness and GitBook block formatting

### Modifying Navigation

To add/remove pages from GitBook navigation, edit the relevant `SUMMARY.md` file:
- `documentation/SUMMARY.md` - Documentation space (main product docs)
- `api-docs/SUMMARY.md` - API Docs space
- `guides-and-tips/SUMMARY.md` - Guides & Tips space

When adding new pages:
1. Create the markdown file in the appropriate location within the space
2. Add the entry to the corresponding `SUMMARY.md` file
3. Ensure the file follows GitBook formatting requirements (frontmatter, proper blocks, etc.)
4. Verify the navigation hierarchy matches the agreed-upon structure

### Validation Workflow
When creating or editing documentation:
1. Ensure proper frontmatter with title and description
2. Use correct GitBook block syntax
3. Verify all blocks are properly closed
4. Check heading hierarchy (no H1 for titles)
5. Validate image paths and alt text
6. Test that nesting rules are followed (no tabs in details, etc.)

## Repository Context

- **Product**: Mailtrap email API/SMTP service
- **Audience**: Developers integrating Mailtrap, users setting up email infrastructure
- **Key Topics**: Email sending APIs, SMTP integration, sandbox testing, DNS configuration, email marketing
- **Documentation Scope**: Product features, integration guides, DNS setup instructions, troubleshooting, FAQs

## Product names

- We should follow the product names as it appears on the website and in marketing materials
- Current names: Email API/SMTP (can be shortened to Email API or API/SMTP), Email Sandbox (can be shortened to Sandbox), Email Marketing (can be shortened to Marketing)

## Content guidelines

- Do not use emojis in main content
- Do not add any content and section if you are not asked to, ask is there is a need a provide a preview before adding it 

## Cross links between spaces (folders)

- If we want from @documentation link to @guides-and-tips our links should look like this: https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/dns-setup/aws-route-53 . This is a link example from @documentation/sending-domain-setup.md to @guides-and-tips/dns-setup/aws-route-53.md . A link vise versa will look like this: https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup 
- If makes sense and use page links as a separate blocks

## OpenAPI
- Never change base URL in Open API specs, a correct base URL has to be displayed
- Base url to be https://send.api.mailtrap.io/ for transactional emails, https://bulk.api.mailtrap.io/api/send for bulk emails, and https://mailtrap.io for the rest
- Use Prism.js language tags for code snippets and OpenApi specs (lang)