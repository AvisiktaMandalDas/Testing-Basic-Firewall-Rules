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

Contents:
block in proto tcp from any to any port 23

4. Loaded Rule in Main pf.conf
sudo nano /etc/pf.conf

Added:
anchor "blocktelnet"
load anchor "blocktelnet" from "/etc/pf.anchors/blocktelnet"

5. Enabled and Reloaded Packet Filter
sudo pfctl -f /etc/pf.conf
sudo pfctl -e

6. Tested Rule
telnet localhost 23 (Connection refused)

7. Allowed SSH (Port 22)
pass in proto tcp from any to any port 22

8. Removed Telnet Block Rule
- Deleted or commented out blocktelnet anchor in /etc/pf.conf
- Reloaded configuration

Firewall Summary
macOS uses a packet filter firewall (pf) to filter network traffic based on defined rules. It helps secure the system by:
-Allowing only trusted connections (e.g., SSH)
-Blocking insecure or unwanted ports (e.g., Telnet)
-This task demonstrated how to create, apply, and test firewall rules, giving hands-on experience with traffic filtering and system protection.




