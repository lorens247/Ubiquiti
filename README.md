# Ubiquiti Device Configuration and MAC ACL Guide

<img src="images/Ubiquiti_Logo.png" alt="Ubiquiti Logo" width="300"/>

## Navigation Menu

- [Home](README.md)
- [Configuration and Troubleshooting](Configuration-Troubleshooting.md)
- [MAC Access Control Lists (ACL)](MAC-ACL.md)


## Configuration

### SSH Access

1. **SSH into the Device**: Connect using `ssh ubnt@<DEVICE_IP>`.

2. **Edit Configuration**: Modify settings like frequencies and IP addresses in `/tmp/system.cfg`.

### Web Interface

1. **Access Web Interface**: Enter the device's IP address in your browser.

2. **Navigate and Configure**: Adjust wireless and network settings under respective sections.

## Troubleshooting

- **SSH Issues**: Ensure device connectivity and correct SSH settings.

- **Configuration Problems**: Save and apply changes properly using `:wq` and `cfgmtd -w -p /etc/`.

- **Network Connectivity**: Test with `ping <IP_ADDRESS>` and check interfaces with `ifconfig`.

## MAC Access Control Lists (ACL)

### SSH Method

1. **SSH Access**: Connect via SSH to edit `/tmp/system.cfg`.

2. **Edit MAC ACL**: Modify deny list entries and apply changes using `cfgmtd -w -p /etc/`.

### Web Interface Method

1. **Web Access**: Navigate to MAC ACL settings under `Security` or `Wireless`.

2. **Configure MAC ACL**: Add MAC addresses to deny list and save changes.

---

This README.md summarizes key steps for configuring, troubleshooting, and implementing MAC Access Control Lists (ACL) on Ubiquiti devices. Refer to Ubiquiti documentation for advanced configurations and support.
