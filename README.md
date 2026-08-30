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
- **Clipboard over SSH** via OSC 52 — copied text lands in the *local*
  machine's clipboard with no helper binary on the remote host
- **Windows renumber** automatically, starting at 1
- Audible bell hooked to a custom alert sound, where one is available
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

No other plugins are in use, so the `prefix + I` step above is only needed
once you add one.

## Notes

### Clipboard

Copying uses tmux's built-in OSC 52 support (`set -g set-clipboard on`) rather
than [tmux-yank](https://github.com/tmux-plugins/tmux-yank). tmux-yank shells
out to `pbcopy`/`clip.exe`/`wl-copy`/`xsel`/`xclip` and has no OSC 52 fallback,
so on a headless host with no X or Wayland its keys bind to nothing but an
error message. OSC 52 sends the text through the SSH stream instead, so it
works the same locally and on every remote box.

The terminal emulator has to allow OSC 52. iTerm2, WezTerm, Kitty, Ghostty and
Windows Terminal all do by default; Alacritty needs it turned on.

### Bell

The `alert-bell` hook plays `~/tmux-alert.wav` through `paplay`. Both the file
and PulseAudio are optional — the hook checks for them and stays silent when
either is missing, so headless hosts get no errors on every bell.
