# Donkey Car LED Control - Usage Guide

Complete usage guide for controlling RGB LEDs on Raspberry Pi via GPIO.

---

## 🚀 Quick Start

All commands require `sudo` for GPIO access:

```bash
sudo python3 led_control.py [command] [options]
```

---

## 💡 Basic Commands

### Turn LEDs On

```bash
# White (default)
sudo python3 led_control.py on

# Specific colors
sudo python3 led_control.py on red
sudo python3 led_control.py on green
sudo python3 led_control.py on blue
sudo python3 led_control.py on yellow
sudo python3 led_control.py on cyan
sudo python3 led_control.py on magenta
sudo python3 led_control.py on orange
sudo python3 led_control.py on purple
sudo python3 led_control.py on pink
sudo python3 led_control.py on lime
sudo python3 led_control.py on teal
sudo python3 led_control.py on warm_white
```

### Turn LEDs Off

```bash
sudo python3 led_control.py off
```

---

## 🎨 Custom RGB Colors

Set any color using RGB values (0-255):

```bash
# Format: custom R G B
sudo python3 led_control.py custom 255 0 0      # Pure red
sudo python3 led_control.py custom 0 255 0      # Pure green
sudo python3 led_control.py custom 0 0 255      # Pure blue
sudo python3 led_control.py custom 255 255 0    # Yellow
sudo python3 led_control.py custom 255 128 0    # Orange
sudo python3 led_control.py custom 128 0 128    # Purple
sudo python3 led_control.py custom 255 192 203  # Pink
sudo python3 led_control.py custom 64 224 208   # Turquoise
sudo python3 led_control.py custom 255 215 0    # Gold
sudo python3 led_control.py custom 255 20 147   # Deep pink
sudo python3 led_control.py custom 75 0 130     # Indigo
sudo python3 led_control.py custom 255 255 255  # White
sudo python3 led_control.py custom 0 0 0        # Off
```

---

## ✨ Special Effects

### Pulse Effect

Fade in and out repeatedly:

```bash
# Format: pulse [color] [duration]
# Duration is for full cycle (fade in + fade out)

# Default: white, 2 seconds
sudo python3 led_control.py pulse

# Colored pulses
sudo python3 led_control.py pulse red
sudo python3 led_control.py pulse blue
sudo python3 led_control.py pulse green
sudo python3 led_control.py pulse orange

# Custom duration
sudo python3 led_control.py pulse red 1.0      # Fast (1 second)
sudo python3 led_control.py pulse blue 3.0     # Slow (3 seconds)
sudo python3 led_control.py pulse green 0.5    # Very fast (0.5 seconds)
```

### Fade Between Colors

Smooth transition from one color to another:

```bash
# Format: fade [color1] [color2] [duration]

# Basic fades
sudo python3 led_control.py fade red blue
sudo python3 led_control.py fade green yellow
sudo python3 led_control.py fade blue purple
sudo python3 led_control.py fade orange pink

# With custom duration
sudo python3 led_control.py fade red blue 2.0
sudo python3 led_control.py fade green yellow 5.0
sudo python3 led_control.py fade white off 1.0

# Multiple color transitions (run multiple commands)
sudo python3 led_control.py fade red orange 1.0
sudo python3 led_control.py fade orange yellow 1.0
sudo python3 led_control.py fade yellow green 1.0
```

---

## 📋 Complete Examples by Use Case

### Status Indicators

```bash
# System starting up
sudo python3 led_control.py pulse orange 1.0

# System ready
sudo python3 led_control.py on green

# Recording data
sudo python3 led_control.py on red

# Autonomous mode active
sudo python3 led_control.py on blue

# Error state
sudo python3 led_control.py pulse red 0.5

# Standby/Off
sudo python3 led_control.py off
```

### Race Mode Sequences

```bash
# Pre-race warm-up
sudo python3 led_control.py pulse yellow 2.0

# Ready to race
sudo python3 led_control.py fade yellow green 1.0

# Racing (solid green)
sudo python3 led_control.py on green

# Finish line
sudo python3 led_control.py pulse green 0.5

# Cool down
sudo python3 led_control.py fade green blue 2.0
```

### Training Mode

```bash
# Collecting data
sudo python3 led_control.py on cyan

# Paused
sudo python3 led_control.py pulse yellow 2.0

# Training complete
sudo python3 led_control.py fade cyan green 1.5
```

### Battery/Power Indicators

```bash
# Full battery (green)
sudo python3 led_control.py on green

# Medium battery (yellow)
sudo python3 led_control.py on yellow

# Low battery (orange)
sudo python3 led_control.py on orange

# Critical battery (flashing red)
sudo python3 led_control.py pulse red 0.5

# Charging
sudo python3 led_control.py fade orange green 2.0
```

### Connection Status

```bash
# Connected to WiFi
sudo python3 led_control.py on green

# Connecting...
sudo python3 led_control.py pulse cyan 1.0

# Disconnected
sudo python3 led_control.py on red

# No connection
sudo python3 led_control.py off
```

### Custom Lighting Effects

```bash
# Rainbow cycle (manual)
sudo python3 led_control.py fade red orange 0.5
sudo python3 led_control.py fade orange yellow 0.5
sudo python3 led_control.py fade yellow green 0.5
sudo python3 led_control.py fade green cyan 0.5
sudo python3 led_control.py fade cyan blue 0.5
sudo python3 led_control.py fade blue purple 0.5
sudo python3 led_control.py fade purple red 0.5

# Strobe effect (rapid on/off)
sudo python3 led_control.py on white
sleep 0.1
sudo python3 led_control.py off
sleep 0.1
# Repeat as needed

# Breathing effect
sudo python3 led_control.py pulse white 3.0

# Police lights (manual)
sudo python3 led_control.py on red
sleep 0.3
sudo python3 led_control.py on blue
sleep 0.3
# Repeat

# Holiday colors
sudo python3 led_control.py fade red green 2.0  # Christmas
sudo python3 led_control.py fade orange purple 2.0  # Halloween
```

---

## 🎯 Integration Examples

### Shell Script Integration

Create a bash script for complex sequences:

```bash
#!/bin/bash
# startup_sequence.sh

echo "Starting Donkey Car..."
sudo python3 led_control.py pulse orange 1.0

echo "Initializing systems..."
sudo python3 led_control.py fade orange yellow 1.0

echo "Systems ready!"
sudo python3 led_control.py fade yellow green 1.0
sudo python3 led_control.py on green
```

### Python Integration

```python
import subprocess
import time

def set_led(command):
    subprocess.run(['sudo', 'python3', 'led_control.py'] + command.split())

# Example usage
set_led('on red')
time.sleep(2)
set_led('fade red green 1.0')
time.sleep(1)
set_led('pulse green 2.0')
```

### Button Control

```bash
# Map button presses to LED commands
# When button 1 pressed:
sudo python3 led_control.py on red

# When button 2 pressed:
sudo python3 led_control.py on green

# When button 3 pressed:
sudo python3 led_control.py off
```

### Cron Job Examples

```bash
# Edit crontab
crontab -e

# Turn on at sunrise (6 AM)
0 6 * * * sudo python3 /home/pi/led_control.py on warm_white

# Turn off at sunset (8 PM)
0 20 * * * sudo python3 /home/pi/led_control.py off

# Pulse every hour
0 * * * * sudo python3 /home/pi/led_control.py pulse blue 2.0
```

---

## 🎨 Available Pre-defined Colors

| Color | RGB Values | Usage Example |
|-------|------------|---------------|
| `white` | 255, 255, 255 | `sudo python3 led_control.py on white` |
| `red` | 255, 0, 0 | `sudo python3 led_control.py on red` |
| `green` | 0, 255, 0 | `sudo python3 led_control.py on green` |
| `blue` | 0, 0, 255 | `sudo python3 led_control.py on blue` |
| `yellow` | 255, 255, 0 | `sudo python3 led_control.py on yellow` |
| `cyan` | 0, 255, 255 | `sudo python3 led_control.py on cyan` |
| `magenta` | 255, 0, 255 | `sudo python3 led_control.py on magenta` |
| `orange` | 255, 128, 0 | `sudo python3 led_control.py on orange` |
| `purple` | 128, 0, 255 | `sudo python3 led_control.py on purple` |
| `pink` | 255, 102, 178 | `sudo python3 led_control.py on pink` |
| `lime` | 128, 255, 0 | `sudo python3 led_control.py on lime` |
| `teal` | 0, 128, 128 | `sudo python3 led_control.py on teal` |
| `warm_white` | 255, 220, 180 | `sudo python3 led_control.py on warm_white` |

---

## 🔧 Command Reference

### Syntax

```bash
sudo python3 led_control.py [command] [arguments]
```

### Commands

| Command | Arguments | Description | Example |
|---------|-----------|-------------|---------|
| `on` | `[color]` | Turn on with color (default: white) | `on red` |
| `off` | none | Turn off LEDs | `off` |
| `custom` | `R G B` | Set custom RGB (0-255 each) | `custom 255 128 0` |
| `pulse` | `[color] [duration]` | Pulse effect (default: white, 2.0s) | `pulse blue 3.0` |
| `fade` | `color1 color2 [duration]` | Fade between colors (default: 1.0s) | `fade red blue 2.0` |
| `help` | none | Show help message | `help` |

---

## 💡 Pro Tips

### Quick Access Aliases

Add to `~/.bashrc`:

```bash
alias led-on='sudo python3 ~/led_control.py on'
alias led-off='sudo python3 ~/led_control.py off'
alias led-red='sudo python3 ~/led_control.py on red'
alias led-green='sudo python3 ~/led_control.py on green'
alias led-blue='sudo python3 ~/led_control.py on blue'
```

Then use:
```bash
led-on
led-red
led-off
```

### Background Effects

Run effects in background:

```bash
# Non-blocking pulse
sudo python3 led_control.py pulse blue 2.0 &

# Non-blocking fade
sudo python3 led_control.py fade red blue 5.0 &
```

### Combining with Other Commands

```bash
# Start telemetry and set LED
sudo python3 led_control.py on green && python3 telemetry_display.py

# Run command and indicate completion
./my_script.sh && sudo python3 led_control.py pulse green 1.0

# Show error state if command fails
./my_script.sh || sudo python3 led_control.py on red
```

---

## ❓ Getting Help

```bash
# Show built-in help
sudo python3 led_control.py help

# Or use standard flags
sudo python3 led_control.py -h
sudo python3 led_control.py --help
```
