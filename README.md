# tmux-config

My personal [tmux](https://github.com/tmux/tmux) configuration.

## Install

```bash
git clone https://github.com/geoffreybyers/tmux-config.git ~/dev/tmux-config
ln -s ~/dev/tmux-config/tmux.conf ~/.tmux.conf
```

Install [tpm](https://github.com/tmux-plugins/tpm) (plugin manager):

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Start tmux and press `prefix + I` to install plugins.

## Highlights

- **Prefix:** `Ctrl-a` (remapped from `Ctrl-b`)
- **50,000 lines** of scrollback history
- **Mouse** enabled for scroll, resize, and click
- **Windows renumber** automatically, starting at 1
- Audible bell hooked to a custom alert sound
- Shift+Enter support via extended keys (CSI u)

## Keybindings

| Key | Action |
|---|---|
| `Ctrl-a` | Prefix |
| `prefix` + `v` | Split vertically (new pane on right) |
| `prefix` + `h` | Split horizontally (new pane below) |
| `prefix` + `r` | Reload config |
| `Alt` + arrow | Move between panes (no prefix needed) |

## Plugins

- [tpm](https://github.com/tmux-plugins/tpm) — plugin manager
- [tmux-yank](https://github.com/tmux-plugins/tmux-yank) — copy mouse selections to system clipboard
