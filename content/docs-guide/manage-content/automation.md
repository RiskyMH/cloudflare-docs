---
pcx_content_type: concept
title: Automation
---

# Automation

Automation allow us to provide more functionality at a lower maintenance cost, as well as enable and support community contributors.

## General principles

When thinking about what to automate in your documentation, look for tasks that are frequent, repetitive, and tedious.

Often, the easiest way to do that is to think through the following questions:

- What do new team members or infrequent contributors get wrong?
- What is part of your standard review checklist? And which steps require an additional level of attention to detail?
- What do stakeholders commonly complain about?

Another component to think about is how often this automation runs:

- What checks need to run on every contribution? Or, another way, what issues would cause you to decline a contribution?
- What checks take a lot of time to run?
- If a check found something wrong, what would be the expected turnaround for a fix?

---

## Examples

### Content maintenance

At Cloudflare, we use several automations to reduce the cost associated with content maintenance.

| Automation | Purpose | Implementation | Runs when |
| --- | --- | --- | --- |
| [Internal link checking](https://github.com/cloudflare/cloudflare-docs/blob/production/bin/crawl.ts) | Evaluate all internal links to make sure they are in the current build. Increases cross linking while reducing maintenance cost. | GitHub Actions | Every commit |
| External link checking | Evaluate external links for broken links or links that redirect to another location. | SEO crawler | Periodically |
| [Header link checking](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/anchor-link-audit.yml) | Evaluate anchor links within our docs to make sure they resolve correctly. | GitHub Actions | Every weekend |
| [API docs link checking](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/api-links-crawl.yml) | Evaluate links to our API docs. | GitHub Actions | Every weekend |
| [Unused images check](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/image-audit.yml) | Flag images that are in our resources, but not currently referenced in our documentation. | GitHub Actions | Every month |

### Reporting

| Automation | Purpose | Implementation | Runs when |
| --- | --- | --- | --- |
| [Label PRs](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/label-pr.yml) | Adds and updates labels related to the content subfolder and size of a pull request. Usefully for rollup reporting and team self-assignment. | GitHub Actions | Every commit |

### Contributor resources

The following resources help contributors and stakeholders when they are making changes to our documentation.

| Automation | Purpose | Implementation | Runs when |
| --- | --- | --- | --- |
| [Build check](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/ci.yml) | Does our docs site build correctly? | GitHub Actions | Every commit |
| [Show before/after links](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/show-changed-files.yml) | Provide a comparison table that shows the current page in production and the changed page in a preview build. | GitHub Actions | Every Pages build |
| [Flag needed redirects](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/comment-changed-filenames.yml) | Comments with a list of changed or deleted files that might need a redirect. | GitHub Actions | Every commit |
| [Infinite redirect check](https://github.com/cloudflare/cloudflare-docs/blob/production/bin/find-infinite-redirects.ts) | Is the commit adding conflicting redirects?  | GitHub Actions | Every commit |
| [Spell check](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/spell-check.yml) | Flag issues with spelling, casing, or insensitive language. | GitHub Actions | Every commit |