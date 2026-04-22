# Tinted Zed

[![Matrix Chat](https://img.shields.io/matrix/tinted-theming:matrix.org)](https://matrix.to/#/#tinted-theming:matrix.org)

[Tinted Theming] color scheme templates for the [Zed] text editor.
Supports [Base16], [Base24], and [Tinted8] scheme systems.

For a preview of the available themes, visit the [Tinted Gallery].

## Table of contents

- [Templates](#templates)
- [Installation](#installation)
- [Usage with Tinty](#usage-with-tinty)
- [Contributing](#contributing)

## Templates

| Template | Scheme System | Description |
| -------- | ------------- | ----------- |
| `default.mustache` | Base16 | 16-color palette with syntax and UI theming |
| `base24.mustache` | Base24 | Extends Base16 with bright terminal variants and darker backgrounds |
| `tinted8.mustache` | Tinted8 | Named palette colors with granular syntax and UI theming properties |

## Usage

### Symlink

Clone the repo and symlink the themes directory so updates are easy to pull:

```sh
git clone https://github.com/tinted-theming/tinted-zed.git ~/.config/zed/tinted-zed
ln -s ~/.config/zed/tinted-zed/themes ~/.config/zed/themes
```

### Manual copy

Copy the contents of the `themes/` directory into `~/.config/zed/themes/`.

### Tinty

[Tinty] is a theme manager for [Tinted Theming] that can apply themes
across multiple applications simultaneously. It supports [Base16],
[Base24], and [Tinted8] scheme systems.

#### Setup

Install [Tinty] and add the following to your
`~/.config/tinted-theming/tinty/config.toml`:

```toml
[[items]]
name = "tinted-zed"
path = "https://github.com/tinted-theming/tinted-zed"
themes-dir = "themes"
supported-systems = ["base16", "base24"]
hook = "cp -f \"$TINTY_THEME_FILE_PATH\" ~/.config/zed/themes/"
```

Then run:

```sh
tinty sync
tinty apply base16-mocha
```

#### Applying themes

```sh
tinty apply base16-mocha      # Apply a specific theme
tinty list                     # List available themes
tinty apply $(tinty list | fzf) # Select a theme interactively (requires fzf)
```

Zed will detect the new theme file in `~/.config/zed/themes/`. You can
then select it from within Zed's theme picker.

For more information on Tinty, refer to the [Tinty documentation].

## Contributing

Contributions are welcome. See the [Tinted Theming] repository for
contribution guidelines and to learn more about the scheme systems.

[Tinted Theming]: https://github.com/tinted-theming/home
[Tinted Gallery]: https://tinted-theming.github.io/tinted-gallery
[Zed]: https://zed.dev
[Base16]: https://github.com/tinted-theming/home/blob/main/styling.md
[Base24]: https://github.com/tinted-theming/base24/blob/main/styling.md
[Tinted8]: https://github.com/tinted-theming/home/blob/main/specs/tinted8/styling.md
[Tinty]: https://github.com/tinted-theming/tinty
[Tinty documentation]: https://github.com/tinted-theming/tinty/blob/main/USAGE.md
