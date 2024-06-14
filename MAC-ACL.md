# Using MAC ACL to Deny Workstations Access to Resources

<img src="images/Ubiquiti_Logo.png" alt="Ubiquiti Logo" width="300"/>

This guide provides instructions on how to configure MAC Access Control Lists (ACL) through both web interface and SSH to deny specific workstations from connecting to a device.

## Prerequisites

- Access to the device's web interface or SSH.
- MAC addresses of the workstations you want to deny.
- Admin credentials for device configuration.

## Web Interface Method

### 1. Access the Device's Web Interface

1. **Open your web browser** and enter the IP address of your device's management interface.

2. **Log in** using your admin credentials.

### 2. Navigate to MAC ACL Configuration

1. **Find the MAC ACL section** in the device's settings. This is usually under Wireless or Security settings depending on the device model.

### 3. Configure MAC ACL

1. **Add MAC addresses** to the deny list. Each MAC address should be entered in the designated field or separated by commas.

   Example:
   ```
   MAC Address 1
   MAC Address 2
   ```

2. **Save** the changes after adding MAC addresses.

### 4. Apply Changes

1. **Apply** the configuration changes. This may involve clicking a "Save" or "Apply Changes" button within the device's interface.

### 5. Verify Configuration

1. **Verify** that the MAC addresses of the denied workstations are correctly added to the MAC ACL list.

## SSH Method

### 1. SSH into the Device

1. **Open your terminal** (Linux/Mac) or **Command Prompt/PowerShell** (Windows).

2. **Connect to the device using SSH**:
   ```sh
   ssh ubnt@<DEVICE_IP>
   ```
   Replace `<DEVICE_IP>` with the IP address of your device.

3. **Enter the password** when prompted.

### 2. Edit MAC ACL Configuration

1. **Navigate to the MAC ACL configuration file**:
   ```sh
   vi /tmp/system.cfg
   ```

2. **Add MAC addresses** to the deny list. Each MAC address should be added on a new line.

   Example:
   ```sh
   deny_mac_file=/etc/deny_mac.list
   ```

3. **Save the changes**:
   - Press `Esc` to exit insert mode if needed.
   - Type `:wq` to save and quit `vi`.

### 3. Apply Changes

1. **Apply the configuration changes**:
   ```sh
   cfgmtd -w -p /etc/
   ```

### 4. Verify Configuration

1. **Verify** that the MAC addresses are correctly added to the deny list.

## Testing

1. **Test connectivity** from the denied workstations to ensure they are unable to connect to the device.

## Conclusion

This guide provides instructions on configuring MAC ACL through both web interface and SSH methods to deny specific workstations from connecting to your device. It ensures enhanced security by controlling access based on MAC addresses effectively.
