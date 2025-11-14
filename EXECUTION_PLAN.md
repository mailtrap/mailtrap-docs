# Documentation Improvement Execution Plan

## Overview
This plan addresses critical formatting issues, missing frontmatter, external images, and content organization across 75 documentation files.

**Total Estimated Time**: 18-24 hours
**Priority**: Critical → High → Medium → Low

---

## 🔴 PHASE 1: CRITICAL FIXES (Week 1 - 8-10 hours)

### Task 1.1: Add Missing Frontmatter (Est: 1 hour)
**Goal**: Add YAML frontmatter to 4 files missing it

#### Subtasks:
1. **Task 1.1.1**: Fix `bounce-categorization.md`
   - [ ] Read file to understand content
   - [ ] Extract H1 title "Bounce Categorization"
   - [ ] Create descriptive description based on content
   - [ ] Add frontmatter with title and description
   - [ ] Change H1 to section heading or remove
   - **Validation**: Check frontmatter syntax, ensure no H1 for page title
   - **Time**: 15 min

2. **Task 1.1.2**: Fix `custom-variables.md`
   - [ ] Read file to understand content
   - [ ] Create title and description
   - [ ] Add frontmatter
   - **Validation**: Verify frontmatter format
   - **Time**: 15 min

3. **Task 1.1.3**: Fix `excluding-specific-links-from-tracking.md`
   - [ ] Read file to understand content
   - [ ] Create title and description
   - [ ] Add frontmatter
   - **Validation**: Verify frontmatter format
   - **Time**: 15 min

4. **Task 1.1.4**: Fix `feedback-loops.md`
   - [ ] Read file to understand content
   - [ ] Create title and description
   - [ ] Add frontmatter
   - **Validation**: Verify frontmatter format
   - **Time**: 15 min

**Checkpoint 1.1**: Run validation check for all files with frontmatter
```bash
grep -L "^---$" documentation/**/*.md | grep -v SUMMARY
```
Expected: Only SUMMARY.md should appear (it's intentionally without frontmatter)

---

### Task 1.2: Fix External Images in Getting Started Guides (Est: 3-4 hours)
**Goal**: Download and replace external images in most-viewed pages first

**Priority Order** (by traffic):
1. getting-started/email-sandbox.md (6 images)
2. getting-started/email-marketing.md (6 images)
3. email-api-smtp/sending-domain-setup.md (19 images - largest batch)

#### Subtasks:

**Task 1.2.1**: Fix `getting-started/email-sandbox.md` (6 images)
1. [ ] Read file to identify all external image URLs
2. [ ] Download each image using WebFetch or curl
3. [ ] Analyze image content to create descriptive names
4. [ ] Rename images following convention: `getting-started-sandbox-[description].png`
5. [ ] Save to `documentation/.gitbook/assets/`
6. [ ] Update file with new image paths
7. [ ] Add descriptive alt text to each image
8. [ ] Convert plain markdown images to `<figure>` tags where needed
9. **Validation**:
   - Check all images load locally
   - Verify alt text is descriptive
   - No external URLs remain in file
10. **Time**: 45-60 min

**Task 1.2.2**: Fix `getting-started/email-marketing.md` (6 images)
1. [ ] Same process as 1.2.1
2. [ ] Naming convention: `getting-started-marketing-[description].png`
3. **Validation**: Same as 1.2.1
4. **Time**: 45-60 min

**Checkpoint 1.2**: Verify getting-started guides
```bash
grep -E "lh7-us\.googleusercontent|d33v4339jhl8k0\.cloudfront" documentation/getting-started/*.md
```
Expected: No results

---

### Task 1.3: Fix External Images in Core API/SMTP Docs (Est: 4-5 hours)

**Task 1.3.1**: Fix `sending-domain-setup.md` (19 images - LARGEST)
1. [ ] Read file completely to understand image context
2. [ ] Group images by section (domain setup steps, DNS verification, etc.)
3. [ ] Download all 19 images
4. [ ] Analyze each image to understand content
5. [ ] Rename with descriptive names: `sending-domains-[action]-[element].png`
6. [ ] Save to `documentation/.gitbook/assets/`
7. [ ] Update all 19 references in file
8. [ ] Add descriptive alt text to each
9. [ ] Convert plain markdown to `<figure>` tags
10. **Validation**:
    - All images load locally
    - Alt text describes image purpose
    - Images match context in text
11. **Time**: 90-120 min

**Task 1.3.2**: Fix `api-integration.md` (7 images)
1. [ ] Same process as 1.3.1
2. [ ] Naming: `api-integration-[feature]-[element].png`
3. **Validation**: Same as 1.3.1
4. **Time**: 45 min

**Task 1.3.3**: Fix `smtp-integration.md` (7 images)
1. [ ] Same process as 1.3.1
2. [ ] Naming: `smtp-integration-[feature]-[element].png`
3. **Validation**: Same as 1.3.1
4. **Time**: 45 min

**Task 1.3.4**: Fix remaining files (8 images across 4 files)
- [ ] suppressions-list.md (3 images)
- [ ] ip-warmup.md (2 images)
- [ ] stats-dashboard.md (1 image) - already fixed
- [ ] email-marketing/statistics.md (1 image) - already fixed
**Time**: 30-45 min

**Checkpoint 1.3**: Verify no external images remain
```bash
grep -r "lh7-us\.googleusercontent\|d33v4339jhl8k0\.cloudfront" documentation/**/*.md
```
Expected: No results

---

### Task 1.4: Add Alt Text to Images with Empty Alt (Est: 2 hours)

**Task 1.4.1**: Create image inventory
1. [ ] Find all images with `alt=""`
2. [ ] List by file
3. [ ] Prioritize by page importance
4. **Output**: CSV or list of files with empty alt text count

**Task 1.4.2**: Add alt text systematically
1. [ ] For each file with empty alt text:
   - Read context around image
   - View image if needed
   - Write descriptive alt text (not generic)
   - Update file
2. **Validation per file**:
   - Alt text describes image content/purpose
   - Alt text is contextual, not generic ("screenshot" is bad, "Domain verification DNS records form" is good)
3. **Time**: 2 min per image × ~48 images = ~90 min

**Checkpoint 1.4**: Verify no empty alt text
```bash
grep -r 'alt=""' documentation/**/*.md
```
Expected: No results or only intentional decorative images

---

## 🟡 PHASE 2: HIGH PRIORITY - SPLIT LARGE FILES (Week 2 - 4-6 hours)

### Task 2.1: Split handlebars-guide.md (Est: 2 hours)
**Goal**: Break 457-line file into 3 focused articles

#### Analysis:
Current structure:
- Lines 1-80: Overview, basic replacement
- Lines 81-280: Conditional helpers (if/unless/each/with)
- Lines 281-360: Order confirmation example
- Lines 361-457: Testing guide

**Task 2.1.1**: Plan new structure
1. [ ] Review current content sections
2. [ ] Define clear boundaries for 3 new files
3. [ ] Plan cross-linking strategy
4. [ ] Update SUMMARY.md structure
5. **Output**: Document with section breakdowns
6. **Time**: 20 min

**Task 2.1.2**: Create `handlebars-basics.md`
Content:
- Overview (what is Handlebars)
- Why use it with Mailtrap
- Basic replacement syntax
- Simple examples
- Link to helpers and testing guides

1. [ ] Create new file with frontmatter
2. [ ] Copy relevant sections from original
3. [ ] Add "Next steps" section with links
4. [ ] Adjust headings (H1 for main sections)
5. **Validation**: File is self-contained, clear purpose
6. **Time**: 30 min

**Task 2.1.3**: Create `handlebars-helpers.md`
Content:
- Overview of helpers
- if/else/if-else with examples
- unless with examples
- each with examples
- with with examples
- Order confirmation complete example
- Link to basics and testing

1. [ ] Create new file with frontmatter
2. [ ] Copy helper sections
3. [ ] Ensure all code examples are complete
4. [ ] Add cross-links
5. **Validation**: All helpers documented with working examples
6. **Time**: 40 min

**Task 2.1.4**: Create `handlebars-testing.md`
Content:
- Overview of testing templates
- Step-by-step testing guide
- Important notes (API tokens, inbox_id)
- Link back to basics and helpers

1. [ ] Create new file with frontmatter
2. [ ] Copy testing sections
3. [ ] Add cross-links
4. **Validation**: Testing process is clear
5. **Time**: 20 min

**Task 2.1.5**: Update parent README.md
1. [ ] Update link from "Handlebars Guide" to "Handlebars Basics"
2. [ ] Add new sub-links for helpers and testing

**Task 2.1.6**: Update SUMMARY.md
```markdown
* [Handlebars with Templates](email-api-smtp/email-templates/handlebars/README.md)
  * [Basics](email-api-smtp/email-templates/handlebars/handlebars-basics.md)
  * [Helpers](email-api-smtp/email-templates/handlebars/handlebars-helpers.md)
  * [Testing](email-api-smtp/email-templates/handlebars/handlebars-testing.md)
```

**Task 2.1.7**: Delete old handlebars-guide.md
1. [ ] Verify all content migrated
2. [ ] Delete file
3. **Validation**: No broken links

**Checkpoint 2.1**: Verify handlebars split
- [ ] All 3 files have proper frontmatter
- [ ] Cross-links work correctly
- [ ] SUMMARY.md updated
- [ ] No broken internal references
- [ ] Old file deleted

---

### Task 2.2: Split sending-domain-setup.md (Est: 1.5 hours)
**Goal**: Break 230-line file into logical sections

**Current structure**:
- Provider links table
- Setting up domain (150+ lines of walkthrough)
- Deleting domains
- Demo restrictions

**Task 2.2.1**: Plan structure
New structure:
1. `README.md` - Overview, when to use, provider links, demo restrictions
2. `domain-setup-walkthrough.md` - Step-by-step setup guide
3. `managing-domains.md` - Deleting, troubleshooting

**Task 2.2.2**: Create folder structure
```bash
mkdir -p documentation/email-api-smtp/sending-domains/
```

**Task 2.2.3**: Create `sending-domains/README.md`
1. [ ] Add frontmatter
2. [ ] Add overview section
3. [ ] Keep provider links table
4. [ ] Add demo restrictions info
5. [ ] Add "Next steps" links
6. **Time**: 25 min

**Task 2.2.4**: Create `sending-domains/domain-setup-walkthrough.md`
1. [ ] Add frontmatter
2. [ ] Copy entire stepper section
3. [ ] Ensure all images and steps are complete
4. **Time**: 30 min

**Task 2.2.5**: Create `sending-domains/managing-domains.md`
1. [ ] Add frontmatter
2. [ ] Copy deletion section
3. [ ] Add troubleshooting tips
4. **Time**: 20 min

**Task 2.2.6**: Update SUMMARY.md
```markdown
* [Sending Domains](email-api-smtp/sending-domains/README.md)
  * [Setup Walkthrough](email-api-smtp/sending-domains/domain-setup-walkthrough.md)
  * [Managing Domains](email-api-smtp/sending-domains/managing-domains.md)
```

**Task 2.2.7**: Update references and delete old file
1. [ ] Search for links to sending-domain-setup.md
2. [ ] Update to point to new structure
3. [ ] Delete old file

**Checkpoint 2.2**: Verify sending-domains split
- [ ] All files have proper frontmatter
- [ ] Navigation works in SUMMARY.md
- [ ] Internal links updated
- [ ] Old file deleted

---

### Task 2.3: Split organization-and-sub-accounts.md (Est: 1.5 hours)
**Goal**: Break 215-line file into focused articles

**Current structure**:
- Overview (40 lines)
- Creating sub-accounts (50 lines)
- Switching accounts (40 lines)
- User management (50 lines)
- Migrating accounts (35 lines)

**Task 2.3.1**: Create folder structure
```bash
mkdir -p documentation/user-management/organization/
```

**Task 2.3.2**: Create `organization/README.md`
1. [ ] Overview
2. [ ] When to use
3. [ ] Key concepts
4. [ ] Links to detailed guides
5. **Time**: 20 min

**Task 2.3.3**: Create `organization/managing-sub-accounts.md`
1. [ ] Creating sub-accounts
2. [ ] Switching between accounts
3. [ ] Deleting sub-accounts
4. [ ] Migrating accounts
5. **Time**: 35 min

**Task 2.3.4**: Create `organization/user-permissions.md`
1. [ ] User management overview
2. [ ] Org-level permissions
3. [ ] Sub-account permissions
4. [ ] Managing users
5. **Time**: 30 min

**Task 2.3.5**: Update SUMMARY.md and references
1. [ ] Update navigation structure
2. [ ] Find and update internal links
3. [ ] Delete old file

**Checkpoint 2.3**: Verify organization split
- [ ] All files have proper frontmatter
- [ ] Clear separation of topics
- [ ] Navigation updated
- [ ] Old file deleted

---

## 🟠 PHASE 3: MEDIUM PRIORITY - FORMATTING (Week 3 - 6-8 hours)

### Task 3.1: Fix Heading Hierarchy (Est: 3 hours)

**Task 3.1.1**: Create heading audit
1. [ ] List all files with heading issues
2. [ ] Document specific issues per file
3. [ ] Prioritize by page traffic

**Task 3.1.2**: Fix files one by one
For each file:
1. [ ] Read file to understand structure
2. [ ] Ensure frontmatter has title (not H1)
3. [ ] Use H1 for major sections only
4. [ ] Use H2 for subsections
5. [ ] Use H3 for details
6. [ ] Don't skip levels
7. **Validation**: Logical hierarchy, no multiple H1s

Files to fix:
- [ ] bounce-categorization.md (already fixed in 1.1.1)
- [ ] automations.md
- [ ] contacts.md
- [ ] 2fa.md
- [ ] 10 others identified

**Time**: 15-20 min per file × 13 files = 3 hours

---

### Task 3.2: Convert Plain Markdown Images to Figures (Est: 2 hours)

**Task 3.2.1**: Find all plain markdown images
```bash
grep -r "!\[.*\](.*)" documentation/**/*.md
```

**Task 3.2.2**: Convert systematically
For each image:
1. [ ] Read context
2. [ ] View image to understand content
3. [ ] Convert to:
```markdown
<figure><img src="path" alt="descriptive alt text"><figcaption><p>Caption</p></figcaption></figure>
```
4. [ ] Write descriptive alt text
5. [ ] Add meaningful caption

**Time**: 5-7 min per image × 19 images = 2 hours

---

### Task 3.3: Review and Potentially Split Medium Files (Est: 2-3 hours)

**Task 3.3.1**: Review `email-marketing/email-templates.md` (192 lines)
1. [ ] Read to understand structure
2. [ ] Compare with API templates structure we created
3. [ ] Decide: keep as is or split similarly
4. [ ] If split: follow same pattern as handlebars split

**Task 3.3.2**: Review `contacts.md` (157 lines)
1. [ ] Read to understand structure
2. [ ] Identify distinct topics (importing, managing, fields, lists)
3. [ ] Decide if splitting improves UX
4. [ ] If split: create folder with focused articles

**Task 3.3.3**: Review `payment-and-billing-faqs.md` (164 lines)
1. [ ] Count Q&As
2. [ ] Group by topic
3. [ ] Consider using {% expand %} blocks for FAQs
4. [ ] Or split into topic-based articles

---

## 🟢 PHASE 4: NICE TO HAVE (Ongoing)

### Task 4.1: Enhance Stub Articles
- [ ] excluding-specific-links-from-tracking.md - add examples
- [ ] custom-variables.md - add use cases
- [ ] campaign-scheduling.md - expand with examples

### Task 4.2: Improve GitBook Block Usage
- [ ] Add {% expand %} to FAQs
- [ ] Add {% tabs %} to code samples
- [ ] Use {% hint %} for important notes

### Task 4.3: Clean Up Unused Images
```bash
cd documentation/.gitbook/assets
rm "unknown.png" "unknown (1).png" "Screenshot.png" "Screenshot (1).png"
```

---

## VALIDATION CHECKLIST (Run After Each Phase)

### After Phase 1:
- [ ] All files have frontmatter (except SUMMARY.md)
- [ ] No external image URLs in documentation
- [ ] No empty alt text on images
- [ ] All images load locally

### After Phase 2:
- [ ] No files over 250 lines (except reference docs)
- [ ] All split articles have clear focus
- [ ] SUMMARY.md reflects new structure
- [ ] No broken internal links
- [ ] Cross-links between related articles work

### After Phase 3:
- [ ] Consistent heading hierarchy across all files
- [ ] All images use `<figure>` tags (except inline icons)
- [ ] Alt text is descriptive and contextual

### Final Validation:
```bash
# Check for external images
grep -r "https://lh7-us\|https://d33v4339jhl8k0" documentation/

# Check for empty alt text
grep -r 'alt=""' documentation/

# Check for missing frontmatter
grep -L "^---$" documentation/**/*.md | grep -v SUMMARY

# Check for plain markdown images (may have legitimate uses)
grep -r "!\[.*\](.*)" documentation/ | grep -v "assets"

# Verify image files exist
# (manual check of image references)
```

---

## RISK MITIGATION

1. **Before starting any task**: Create git branch
   ```bash
   git checkout -b docs/formatting-improvements
   ```

2. **After each checkpoint**: Commit changes
   ```bash
   git add .
   git commit -m "Phase 1.1: Add frontmatter to 4 files"
   ```

3. **Backup external images**: Before replacing, save originals to temp folder
   ```bash
   mkdir -p /tmp/gitbook-external-images/
   ```

4. **Test image downloads**: Verify image quality and content before replacing

5. **Keep audit trail**: Document each change in commit messages

---

## SUCCESS METRICS

- ✅ 0 files missing frontmatter (except SUMMARY.md)
- ✅ 0 external image URLs
- ✅ 0 empty alt text attributes
- ✅ 0 files over 300 lines (except generated docs)
- ✅ Consistent heading hierarchy across all files
- ✅ 90%+ images using proper `<figure>` syntax
- ✅ Improved documentation navigation (from user feedback)
- ✅ No broken links after restructuring

---

## TIME TRACKING TEMPLATE

Use this to track actual time vs estimated:

| Task | Estimated | Actual | Notes |
|------|-----------|--------|-------|
| 1.1.1 | 15 min | ___ | |
| 1.1.2 | 15 min | ___ | |
| ... | | | |

---

## QUESTIONS TO RESOLVE BEFORE STARTING

1. Should we create a separate `/handlebars/` folder or keep under `/email-templates/`?
2. For external images: Should we fetch high-res versions or keep current quality?
3. For FAQs: Use {% expand %} blocks or split into separate articles?
4. Priority order: Any specific pages that are more critical due to traffic?
5. Git workflow: Single PR or multiple PRs per phase?

---

**Next Step**: Review this plan, confirm approach, and I'll begin with Phase 1, Task 1.1 (adding frontmatter to 4 files).
