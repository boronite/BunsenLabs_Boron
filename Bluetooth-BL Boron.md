# Bluetooth Fix for BunsenLabs After Debian 13 Live Session

## Quick Commands

```bash
# 1. Reset Bluetooth
sudo systemctl stop bluetooth && sudo rm -rf /var/lib/bluetooth/* && sudo systemctl start bluetooth

# 2. Reinstall Packages
sudo apt reinstall bluez blueman pipewire-pulse pipewire-audio libspa-0.2-bluetooth

# 3. Reload Driver
sudo rmmod btusb && sudo modprobe btusb

# 4. Manual Pairing
bluetoothctl
# In interactive mode:
#   power on
#   agent on
#   scan on
#   pair [MAC]
#   connect [MAC]
#   trust [MAC]
#   (Ctrl+D to exit)

# 5. Restart PipeWire
systemctl --user restart pipewire

# 6. Check Audio
pactl list sinks | grep -i bluetooth

# 7. Full Reinstall (if needed)
sudo apt purge bluez* blueman pipewire* && sudo apt install bluez blueman pipewire pipewire-pulse

# 8. Check Logs
dmesg | grep -i blue
