# archdotfiles

My personal dotfiles for a Hyprland-based Arch Linux setup. Built for a minimal, keyboard-driven Wayland workflow.

![Made for Hyprland](https://img.shields.io/badge/WM-Hyprland-blue)
![Arch Linux](https://img.shields.io/badge/OS-Arch%20Linux-1793D1)

## Preview

> Add a screenshot of your desktop here, e.g. `backgrounds/preview.png`
>
> ```md
> ![Desktop Screenshot](backgrounds/preview.png)
> ```

## What's Included

| Component     | Tool         | Description                          |
|---------------|--------------|---------------------------------------|
| Compositor    | [Hyprland](https://hyprland.org/)     | Dynamic tiling Wayland compositor |
| Lock Screen   | Hyprlock     | Custom lock screen config            |
| Wallpaper     | Hyprpaper    | Wallpaper daemon config              |
| Status Bar    | Waybar       | System status bar                    |
| App Launcher  | Wofi         | Application launcher / menu          |
| Terminal      | Kitty        | GPU-accelerated terminal emulator    |
| Editor        | Neovim       | Configured with Lua                  |
| Shell Prompt  | Starship     | Cross-shell prompt                   |
| Multiplexer   | Tmux         | Terminal session/window management   |
| GTK Theme     | GTK 3.0      | GTK application theming              |

## Directory Structure

```
archdotfiles/
├── hyprland/     # Hyprland compositor config
├── hyprlock/      # Lock screen config
├── hyprpaper/     # Wallpaper daemon config
├── waybar/        # Status bar config + styling
├── wofi/          # App launcher config + styling
├── kitty/         # Terminal emulator config
├── nvim/          # Neovim configuration (Lua)
├── starship/      # Shell prompt config
├── tmux/          # Terminal multiplexer config
├── gtk-3.0/       # GTK theming
└── backgrounds/   # Wallpapers
```

## Installation

This repo is managed with [GNU Stow](https://www.gnu.org/software/stow/), which symlinks each package's files into `~/.config/` (or `$HOME`) instead of copying them — so pulling updates is just a `git pull`.

> ⚠️ Back up or remove any existing configs for these apps before stowing, since Stow will refuse to symlink over a file that already exists.

### 1. Install Stow

```bash
sudo pacman -S stow
```

### 2. Clone the repo

```bash
git clone https://github.com/0xS0l0/archdotfiles.git
cd archdotfiles
```

### 3. Stow the packages you want

Each top-level folder is its own Stow "package." Run from the repo root:

```bash
stow hyprland
stow hyprlock
stow hyprpaper
stow waybar
stow wofi
stow kitty
stow nvim
stow starship
stow tmux
stow gtk-3.0
```

Or stow everything at once:

```bash
stow */
```

To remove (unlink) a package's symlinks:

```bash
stow -D hyprland
```

To re-stow after making changes (unlink + relink):

```bash
stow -R hyprland
```

> **Note:** Stow mirrors each package's internal folder structure into the target directory (`$HOME` by default). Make sure each package folder in this repo mirrors the path it should land at — e.g. `nvim/.config/nvim/init.lua` so that `stow nvim` places it at `~/.config/nvim/init.lua`. If your packages currently look like `nvim/init.lua` instead, you'll want to restructure them to include the `.config/` prefix, or point Stow's target directly, e.g. `stow -t ~/.config nvim`.

### Dependencies

Make sure the following are installed on your Arch system before stowing these configs:

```bash
sudo pacman -S hyprland hyprlock hyprpaper waybar wofi kitty neovim starship tmux stow
```

## Key Features

- Fully keyboard-driven Wayland workflow with Hyprland
- Lightweight, minimal status bar via Waybar
- Custom lock screen and wallpaper handling
- Neovim configured for a fast, distraction-free editing experience
- Consistent theming across terminal, launcher, and GTK apps

## Notes

- These dotfiles are tailored to my personal workflow and hardware — you may need to tweak monitor resolutions, keybindings, and paths to fit your own system.
- Feel free to fork and adapt to your own setup.

## License

MIT — feel free to use, modify, and share.
