# Testing-Basic-Firewall-Rules

# Objective
Configure and test basic firewall rules to allow or block network traffic using macOS built-in tools.

# Tools Used
- macOS Firewall (GUI-based)
- `pfctl` (Packet Filter command-line tool)
- Terminal
- Telnet (installed via Homebrew)

# Steps Performed
1. Enabled macOS Firewall
- System Settings → Network → Firewall → Turned ON

2. Blocked Incoming Connections via GUI
- Clicked Options in Firewall settings
- Added Terminal or test app and set it to Block incoming connections

3. Created Custom Rule to Block Port 23 (Telnet)
```bash
sudo nano /etc/pf.anchors/blocktelnet
