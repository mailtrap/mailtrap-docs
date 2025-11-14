# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a GitBook documentation repository for Mailtrap, an email API/SMTP service. The documentation is organized into three main sections:

- **`documentation/`** - Primary product documentation covering Email API/SMTP, Email Sandbox, and Email Marketing
- **`developers/`** - Developer-focused API documentation and integration guides
- **`guides-and-tips/`** - DNS setup guides for various providers (AWS Route 53, Cloudflare, etc.)

Each section contains:
- `SUMMARY.md` - GitBook table of contents defining the navigation structure
- `README.md` - Landing page for that section
- Nested markdown files organized by feature/topic

## GitBook Formatting Requirements

This repository uses GitBook-specific markdown syntax. A `gitbook-assistant` skill is available in `.claude/skills/gitbook-assistant/` with comprehensive formatting rules, templates, and validation capabilities.

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

## Documentation Structure Patterns

### Image Formatting
Images use specific GitBook attributes:
```html
<div align="left" data-with-frame="true">
  <img src="URL" alt="description" width="563">
</div>
```
or with captions:
```html
<div align="left" data-with-frame="true">
  <figure>
    <img src="URL" alt="" width="563">
    <figcaption><p>Caption text</p></figcaption>
  </figure>
</div>
```

### Link Buttons
GitBook supports custom link styling:
```html
<a href="URL" class="button primary">Button Text</a>
<a href="URL" class="button secondary">Button Text</a>
```

### Content Organization
- Use `SUMMARY.md` to define navigation structure
- Maintain consistent nested folder structure matching SUMMARY.md hierarchy
- Place shared assets in `.gitbook/assets/` directory

## Working with This Repository

Since this is a documentation-only repository:
- No build, test, or lint commands
- No package managers or dependencies
- Changes are validated through GitBook's preview/publish system
- Focus on markdown syntax correctness and GitBook block formatting

### Modifying Navigation
To add/remove pages from GitBook navigation, edit the relevant `SUMMARY.md` file:
- `documentation/SUMMARY.md` - Main product docs
- `developers/SUMMARY.md` - Developer docs
- `guides-and-tips/SUMMARY.md` - Guides and tips

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
