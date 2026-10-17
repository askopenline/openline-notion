# Openline OS Visual Assets

The official public asset library and badge generator for Openline's company operating system in Notion. Maintained by [Openline](https://openline.com) in [askopenline/openline-notion](https://github.com/askopenline/openline-notion).

## Scope

This repository holds visual resources used by Openline OS, including navigation badges, section graphics, covers, and supporting images. It is not an export of the private Notion workspace, its databases, or its access permissions.

The separate `openline-audit-shots` company repository is private. Use this public repository for assets that have been reviewed for public hosting, rather than assuming a private GitHub raw URL will render in Notion.

## Repository guide

| Location | Purpose |
| --- | --- |
| [`badge-system/badges.json`](badge-system/badges.json) | Declarative badge and supporting-asset definitions |
| [`badge-system/gen_badge.py`](badge-system/gen_badge.py) | Shared image renderer |
| [`badge-system/build_all.py`](badge-system/build_all.py) | Batch generation |
| [`badge-system/README.md`](badge-system/README.md) | Generator usage and requirements |
| [`os-nav/`](os-nav/) | Navigation and related generated images |
| [`staff/`](staff/) | Staff-area visual assets |
| [`covers/`](covers/) | Workspace cover artwork |
| [`shots/`](shots/), [`out_images/`](out_images/) | Supporting captures and prepared images |
| [`BADGE-SYSTEM.md`](BADGE-SYSTEM.md), [`CONTEXT.md`](CONTEXT.md) | Earlier design and maintenance context |

## Generate badges

Use Python 3, Pillow, and the font expected by the renderer. Keep the JSON manifest as the source of truth and review the generator notes before changing styles or presets.

```sh
git clone https://github.com/askopenline/openline-notion.git
cd openline-notion
python3 -m venv .venv
. .venv/bin/activate
pip install Pillow
python3 badge-system/build_all.py --dir os-nav
```

The command writes generated files, so review the diff before committing. Confirm labels, dimensions, transparency, contrast, and icon alignment; a successful script exit is not a visual review.

## Embed company-hosted assets

Use a reviewed image from the company repository. For example, a navigation image can follow this URL pattern:

```text
https://raw.githubusercontent.com/askopenline/openline-notion/main/os-nav/badge-strategic-tasks.png
```

For predictable rendering, prefer a full commit SHA instead of `main` when updating Notion. A changed GitHub asset can remain stale in both GitHub's delivery cache and Notion's image proxy; when needed, use the reviewed commit URL and replace the affected Notion image reference.

Stable filenames are useful, but overwriting a PNG does not guarantee that every existing embed refreshes immediately. Existing Notion pages and earlier repository URLs remain unchanged until an explicit workspace update is made.

## Maintenance and public-content review

1. Edit the manifest rather than hand-redrawing individual generated badges.
2. Keep existing slugs stable unless their consumers will be updated.
3. Regenerate the affected assets and inspect the output.
4. Check images and captures for customer data, credentials, internal notes, and other non-public content before committing.
5. Commit approved files, verify the intended public URLs, and update Notion separately when needed.

The company repository copy does not rewrite Notion blocks, relations, databases, or existing embeds. Historical runbooks should be interpreted in that context, not as evidence that a hosting migration has already occurred.

## Ownership and use

Openline maintains the company-created graphics and generator documentation in this library. Public hosting is intended to support Openline materials; third-party fonts, icons, screenshots, and other incorporated resources retain their respective rights and notices.
