![banner-light](https://raw.githubusercontent.com/uloco/bluloco.nvim/main/screenshots/banner-light.svg#gh-light-mode-only)
![banner-dark](https://raw.githubusercontent.com/uloco/bluloco.nvim/main/screenshots/banner-dark.svg#gh-dark-mode-only)

# Bluloco for lich

## Overview

A fancy and sophisticated designer theme for [lich](https://github.com/lichdotdev/lich),
with due regards to aesthetics, contrast and readability. There is a light and
dark variant.

This is a port of [uloco/bluloco.nvim](https://github.com/uloco/bluloco.nvim) by
[Umut Topuzoğlu](https://github.com/uloco), itself a port of the Visual Studio
Code themes [Bluloco Light](https://github.com/uloco/theme-bluloco-light) and
[Bluloco Dark](https://github.com/uloco/theme-bluloco-dark).

## Support the original author

Bluloco is Umut's work, and keeping it updated takes a lot of their time. If you
like it, please consider supporting them directly:

<a href="https://www.buymeacoffee.com/umipaloomi" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-violet.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a> <a href="https://www.paypal.com/donate/?hosted_button_id=YSDKWM2D66GZJ" target="_blank"><img src="https://pics.paypal.com/00/s/OGRmNzQwNTMtZGNiYS00MTIzLWE1ZWUtNWI2ZDdhMGUwMWVm/file.PNG" alt="PayPal Donate" style="height: 60px !important;" ></a>

## Variants

| Theme | `id` | `scheme` |
|---|---|---|
| Bluloco Dark | `bluloco-dark` | dark |
| Bluloco Light | `bluloco-light` | light |

## Installation

lich installs a theme repository from its URL — nothing to download or copy by
hand:

1. Open lich and go to **Settings → Appearance**.
2. Next to **Theme**, click **Import**.
3. Paste `https://github.com/lichdotdev/bluloco-lich` and click **Install**.
4. Pick **Bluloco Dark** or **Bluloco Light** in the theme picker. The terminal
   picker defaults to **Match app theme**, so one pick dresses the interface and
   the terminal panes alike.

Later releases are taken with **Update** on the theme's row.

### Local install

An absolute path is an accepted remote, so a clone installs the same way:

```bash
git clone https://github.com/lichdotdev/bluloco-lich.git
```

Then paste the absolute path of the clone into **Settings → Appearance → Import**.

## How the palette maps

The app tokens take the colors upstream uses for the same roles in
[`lua/lush_theme/bluloco.lua`](https://github.com/uloco/bluloco.nvim/blob/main/lua/lush_theme/bluloco.lua);
the derived greys are upstream's `shade`/`grey` steps resolved to hex.

| Role | Dark | Light | Upstream |
|---|---|---|---|
| `background` / `foreground` | `#282c34` / `#abb2bf` | `#f9f9f9` / `#383a42` | `Normal` |
| `sidebar`, `popover` | `#21242d` | `#ecedee` | `bgFloat` (`NormalFloat`, `NvimTreeNormal`) |
| `card` | `#23272f` | `#ececec` | the tab bar of the kitty port |
| `accent` | `#354052` | `#d8e2e8` | `CursorLine` (`grey7`) |
| `primary` | `#3691ff` | `#275fe4` | `tag` blue |
| `ring` | `#10b1fe` | `#0099e1` | `keyword` blue, kept off `primary` |
| `muted-foreground` | `#8f9aae` | `#676a77` | terminal bright black — `comment` is too faint for 12px meta text |
| `destructive` | `#ff2e3f` | `#d52753` | `error` / `type` red |

The terminal palette is the upstream
[kitty port](https://github.com/uloco/bluloco.nvim/tree/main/terminal-themes/kitty)
verbatim, cursor and selection included.

The `syntax` colors, which lich's native window uses for code in the review,
diff and file views, are the `tokenColors` of the official VS Code themes
[Bluloco Dark](https://github.com/uloco/theme-bluloco-dark) and
[Bluloco Light](https://github.com/uloco/theme-bluloco-light) (non-italic
variants), each TextMate scope mapped to the equivalent highlighting tag.

### Status tones

`tone-pass` and `tone-wait` are what lich 0.53.0 reads for "passed" and "waiting
on you", set at 12px where WCAG asks 4.5:1. Where the palette value did not
clear that against the card, its lightness was moved and its hue kept.

| Variant | `tone-pass` | `tone-wait` |
|---|---|---|
| Bluloco Dark | `#3fc56b` (`method` green) | `#f9c859` (`string` yellow) |
| Bluloco Light | `#1d7b3d` (`method` green, darkened) | `#b24d00` (`warning` orange, darkened) |

## Thanks to

- [Umut Topuzoğlu (uloco)](https://github.com/uloco) — Bluloco, the original
  palette and [bluloco.nvim](https://github.com/uloco/bluloco.nvim).
  [Buy them a coffee](https://www.buymeacoffee.com/umipaloomi)!
- [omartelo](https://github.com/omartelo) — lich port

## Contributing

Each variant is one lich theme file — `bluloco-dark.json`, `bluloco-light.json`
— beside the `lich-theme.json` manifest that carries the pack's version. There is
no generator: colors are edited directly in the theme files.

1. Fork the repo.
2. Edit the relevant variant file.
3. Validate the **whole directory** — a repository installs all or nothing:
   `node validate.mjs .` (ships with the lich `theme` skill).
4. Bump `version` in `lich-theme.json` in the same commit. An unbumped version
   ships nothing: **Update** compares only that number.
5. Open a PR.

## License

[LGPL-3.0](./LICENSE), the same as [bluloco.nvim](https://github.com/uloco/bluloco.nvim).
