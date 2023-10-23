# Fix read-only root file system
This script is designed to automatically repair a read-only root file system on OpenWrt devices. It checks if the file system is in read-only mode and initiates the repair process using the **e2fsck** command. 
This script also detects where the system root partition is located before run the command. 
If the repair is successful, it restores the file system to read-write mode and optionally performs a reboot to apply the changes.

**Usage Instructions:**
1. Ensure you have access to an OpenWrt device with a file system that needs repair.
2. Connect to the device using SSH or a terminal.
3. Install the script by running the following command:
  ```
  wget --no-check-certificate https://raw.githubusercontent.com/frizkyiman/fix-read-only/main/install.sh -O /tmp/install.sh && chmod +x /tmp/install.sh && /tmp/install.sh
  ```

4. Run the script manually with the following command:
  ```
  /usr/bin/repair_ro
  ```
6. Add script to startup (optional, already include when installing)
  ```
  sed -i '/exit 0/i /usr/bin/repair_ro' /etc/rc.local
  ```
You can also call this script with the command from SSH or terminal:
```
repair_ro
```

Note: You need reboot manually if the script fail to reboot after fixing the ro file system.

  The script will automatically check if the file system is read-only, repair it if needed, and restore it to read-write mode.
  
  **Note:** If the repair is successful, the script will reboot the system to apply the changes.
