# Openline OS Badge Generator

> Openline company documentation: maintained in [askopenline/openline-notion](https://github.com/askopenline/openline-notion). See the [repository README](../README.md) for ownership, scope, and release boundaries.

The shared renderer and manifest for Openline OS navigation badges and related visual assets. Maintained as part of the official [Openline public visual library](https://github.com/askopenline/openline-notion).

## Files and requirements

| File | Purpose |
| --- | --- |
| [`badges.json`](badges.json) | Labels, slugs, colors, icons, and presets |
| [`gen_badge.py`](gen_badge.py) | Image renderer |
| [`build_all.py`](build_all.py) | Batch build |

Use Python 3, Pillow, and the font expected by `gen_badge.py`. Check the renderer's font paths on a new workstation; copying the repository does not install system fonts.

## Generate and review

From the repository root:

```sh
python3 badge-system/build_all.py --dir os-nav
```

The manifest includes the badge list and, where present, additional asset presets. Review the generated PNGs for correct labels, dimensions, alpha, contrast, icon alignment, and consistency before committing.

Add or edit entries in `badges.json`, then regenerate rather than hand-editing output images. Preserve stable slugs unless the consuming Notion blocks will be updated.

## Public embedding

Use URLs under the official company repository for newly configured public assets:

```text
https://raw.githubusercontent.com/askopenline/openline-notion/main/os-nav/<slug>.png
```

For an intentional Notion refresh, pin the reviewed full commit SHA and replace the affected image reference when necessary. GitHub delivery and Notion's image proxy can both cache an older image, so overwriting a filename is not a guarantee of an immediate workspace-wide refresh.

This repository copy does not edit existing Notion pages or earlier image URLs. Public hosting is appropriate only for assets reviewed for disclosure; never move private captures here just to bypass an authentication requirement.
