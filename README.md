# Custom Music Lyrics Bar for Waybar

A customized Waybar configuration that displays music player controls and real-time song lyrics with a sleek, dark theme.

## Features

- **Music Player Integration** - Shows currently playing track (title - artist)
- **Playback Controls** - Previous, Play/Pause, Next buttons with intuitive icons
- **Live Lyrics Display** - Real-time song lyrics displayed as you listen
- **Status Awareness** - Different icons for playing vs paused states
- **Tooltips** - Hover information showing player status and dynamic details
- **Dark Theme** - Minimal, distraction-free dark color scheme
- **Nerd Font Icons** - Beautiful monospace icons for a polished look

## Color Scheme

- **Text Color**: `rgb(197, 202, 231)` (Light lavender/gray)
- **Background Color**: `rgb(20, 21, 27)` (Almost pure black)
- **Font**: CaskaydiaMono Nerd Font at 12px

## Installation

### 1. Install Required Dependencies

#### On Arch Linux (or Arch-based distros):
```bash
sudo pacman -S waybar playerctl
yay -S waybar-lyric-git  # or use another AUR helper
```

#### On Ubuntu/Debian:
```bash
sudo apt install waybar playerctl
# For waybar-lyric, you may need to build from source or check your distro's repos
```

#### On Fedora:
```bash
sudo dnf install waybar playerctl
# For waybar-lyric, check available packages or build from source
```

### 2. Install the Nerd Font

Download and install CaskaydiaMono Nerd Font:
```bash
# On Linux, fonts typically go in ~/.local/share/fonts/
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts

# Download the font (example for CaskaydiaMono)
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.0.0/CascadiaMono.zip
unzip CascadiaMono.zip
rm CascadiaMono.zip

# Refresh font cache
fc-cache -fv ~/.local/share/fonts/
```

### 3. Set Up Music Player Daemon

Ensure you have a music player installed and the D-Bus service running:

```bash
# Install a music player (if not already installed)
# Examples: mpv, VLC, Spotify, etc.

# Make sure playerctld is running (usually auto-starts)
systemctl --user start playerctld
systemctl --user enable playerctld
```

### 4. Copy Configuration Files

Copy the configuration to your Waybar config directory:

```bash
# Create waybar config directory if it doesn't exist
mkdir -p ~/.config/waybar

# Copy config and styles
cp config.json ~/.config/waybar/
cp styles.css ~/.config/waybar/
```

Or if you want to place them in your project directory:
```bash
# In your waybar configuration
# Add to your waybar config:
# --config /path/to/Custom-music-lyrics-bar/config.json
# --css /path/to/Custom-music-lyrics-bar/styles.css
```

### 5. Configure Your Window Manager

Add Waybar to your window manager's startup sequence:

**For Sway (wlroots-based WMs):**
```
# Add to ~/.config/sway/config
exec waybar
```

**For Hyprland:**
```
# Add to ~/.config/hypr/hyprland.conf
exec-once = waybar
```

**For other WMs:**
Refer to your WM's documentation for startup scripts.

### 6. Reload/Restart Waybar

After installation and configuration:
```bash
# If waybar is already running, reload it
pkill waybar && waybar &

# Or restart your window manager
```


## Configuration Details

### Modules Enabled

- **custom/lyrics** - Real-time lyrics display via waybar-lyric
- **mpris** - Music player info and controls
- **mpris#player-prev** - Previous track button
- **mpris#pauseplay** - Play/Pause button
- **mpris#player-next** - Next track button

### Customization

#### Change Colors
Edit `styles.css`:
```css
* {
  color: rgb(197, 202, 231);           /* Change text color */
  background-color: rgb(20, 21, 27);   /* Change background color */
}
```

#### Change Font
Edit `styles.css`:
```css
* {
  font-family: "Your Font Name";
  font-size: 12px;  /* Adjust size as needed */
}
```

#### Change Bar Position
Edit `config.json`:
```json
{
  "position": "bottom",  /* or "top", "left", "right" */
  "height": 26           /* Adjust height in pixels */
}
```

#### Change Music Player
Edit `config.json` and replace `"playerctld"` with your player's name:
```json
"mpris": {
  "player": "spotify",  /* or "mpv", "vlc", etc. */
}
```

## Dependencies Summary

| Tool | Purpose |
|------|---------|
| **waybar** | Main bar application |
| **playerctl** | Command-line music player control |
| **playerctld** | D-Bus daemon for playerctl |
| **waybar-lyric** | Real-time lyrics display module |
| **CaskaydiaMono Nerd Font** | Font with icon glyphs |

## License

Free to use and modify for personal use.