# Ubiquiti Device Configuration and Troubleshooting Guide using Terminal

This guide provides step-by-step instructions for configuring and troubleshooting Ubiquiti devices using the terminal.
It covers SSH access, various configuration changes such as frequency, WAN/LAN IPs, device name, and basic troubleshooting steps.

## Prerequisites

- SSH client installed (e.g., Terminal for Mac/Linux, PuTTY for Windows)
- IP address of the Ubiquiti device (`192.168.1.20` in this example)
- Admin credentials (default username: `ubnt`, default password: `Ubnt12345.`)

## SSH Access
### Logging into the Device

1. **Open your terminal (Linux/Mac) or Command Prompt/PowerShell (Windows)**.

2. **Run the SSH command**:
   ```sh
   ssh ubnt@192.168.1.20
   ```
   Replace `192.168.1.20` with the actual IP address of your Ubiquiti device.

3. **Enter the password when prompted**.

If you encounter an error such as `no matching host key type found`, you can add the `HostKeyAlgorithms` option:
```sh
ssh -o HostKeyAlgorithms=+ssh-rsa,ssh-dss ubnt@192.168.1.20
```

## Configuration

### Editing Configuration Files

1. **Open the configuration file**:
   ```sh
   vi /tmp/system.cfg
   ```

2. **Navigate and Edit**:
   - Press `/` to start a search in `vi`.
   - Type the setting you want to modify and press `Enter`.
   - Use the arrow keys to navigate and press `i` to enter insert mode.
   - Make your changes.

3. **Save and Exit**:
   - Press `Esc` to ensure you're in command mode.
   - Type `:wq` and press `Enter` to save and quit.

### Example Configurations

#### Changing Frequency

To change the frequency:

1. **Open the configuration file**:
   ```sh
   vi /tmp/system.cfg
   ```

2. **Modify or Add the Frequency Setting**:
   - Example to set the frequency to 5805 MHz:
     ```sh
     radio.1.freq=5805
     ```

3. **Save and Exit**:
   - Press `Esc`, type `:wq`, and press `Enter`.

#### Changing WAN and LAN IPs

To change the WAN and LAN IPs:

1. **Open the configuration file**:
   ```sh
   vi /tmp/system.cfg
   ```

2. **Modify the IP settings**:
   - Example to change WAN IP:
     ```sh
     wan.1.ipaddr=192.168.0.100
     ```
   - Example to change LAN IP:
     ```sh
     lan.1.ipaddr=192.168.1.1
     ```

3. **Save and Exit**:
   - Press `Esc`, type `:wq`, and press `Enter`.

#### Changing Device Name

To change the device name:

1. **Open the configuration file**:
   ```sh
   vi /tmp/system.cfg
   ```

2. **Modify the device name setting**:
   - Example to change the device name:
     ```sh
     system.device.hostname=MyUbiquitiDevice
     ```

3. **Save and Exit**:
   - Press `Esc`, type `:wq`, and press `Enter`.

## Applying Changes

1. **Write the changes to the system configuration**:
   ```sh
   cfgmtd -w -p /etc/
   ```

2. **Reboot the device to apply changes**:
   ```sh
   reboot
   ```

## Troubleshooting

### Common Issues

- **Unable to SSH into Device**:
  - Ensure the device is powered on and connected to the network.
  - Verify the IP address and credentials.
  - If you receive a host key error, try adding `-o HostKeyAlgorithms=+ssh-rsa,ssh-dss` to your SSH command.

- **Changes Not Applying**:
  - Ensure you run `cfgmtd -w -p /etc/` after editing the configuration file.
  - Reboot the device to apply changes.

### Logs and Diagnostics

1. **View System Logs**:
   ```sh
   cat /var/log/messages
   ```

2. **Check Current Configuration**:
   ```sh
   cat /tmp/system.cfg
   ```

3. **Network Diagnostics**:
   - **Ping a host**:
     ```sh
     ping 8.8.8.8
     ```
   - **Check network interfaces**:
     ```sh
     ifconfig
     ```

## Conclusion

This guide provides the essential commands and steps for configuring and troubleshooting Ubiquiti devices via the terminal. For more advanced configurations and diagnostics, refer to the official Ubiquiti documentation or seek assistance from Ubiquiti support.
