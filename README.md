# Terminal Screensaver

A terminal-based screensaver adapted from [Omarchy](https://github.com/basecamp/omarchy) and modified to work on Ubuntu-based distros. Uses [TerminalTextEffects (TTE)](https://github.com/ChrisBuilds/terminaltexteffects) to display animated text effects in fullscreen Alacritty windows. It launches one window per monitor and dismisses on any keyboard or mouse input.

## Dependencies

- [Alacritty](https://alacritty.org/) - terminal emulator
- [TerminalTextEffects (TTE)](https://github.com/ChrisBuilds/terminaltexteffects) - text animation engine
- `xrandr` - for multi-monitor detection
- `notify-send` - for toggle notifications (usually part of `libnotify`)

## Installation

1. Clone the repo:

   ```sh
   git clone git@github.com:dustinmartin/terminal-screensaver.git
   cd terminal-screensaver
   ```

2. Install TTE:

   ```sh
   pipx install terminaltexteffects
   ```

3. Set up idle-triggered activation by copying the autostart entry and updating the path:

   ```sh
   cp autostart/screensaver-idle.desktop ~/.config/autostart/
   ```

   Edit `~/.config/autostart/screensaver-idle.desktop` and update the `Exec=` path to point to your cloned location.

## Usage

### Launch manually

```sh
bin/screensaver-launch
```

Pass `force` to ignore the disabled state:

```sh
bin/screensaver-launch force
```

### Toggle on/off

```sh
bin/screensaver-toggle
```

This creates/removes a state file at `~/.local/state/screensaver/toggles/screensaver-off`. When the file exists, idle-triggered activation is suppressed. A desktop notification confirms the current state.

### Dismiss

Press any key or move the mouse to exit the screensaver.

## Customization

- **Display text** - Edit `config/screensaver.txt` with your own ASCII art or text.
- **Alacritty appearance** - Modify `config/alacritty-screensaver.toml` to change font size, colors, or window settings.
- **TTE options** - Edit `bin/screensaver-cmd` to change the frame rate, exclude specific effects, or pin a single effect instead of using `--random-effect`.
- **Idle timeout** - Set `SCREENSAVER_TIMEOUT_MS` environment variable (default: 300000 = 5 minutes).
