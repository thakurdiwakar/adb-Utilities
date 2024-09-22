# Comprehensive ADB Command Guide

## 1. Device Connection & Server Management
- **List connected devices (with details):**
  ```bash
  adb devices -l
  ```
- **Start the ADB server:**
  ```bash
  adb start-server
  ```
- **Kill the ADB server:**
  ```bash
  adb kill-server
  ```
- **Set up ADB server via Wi-Fi:**
  ```bash
  adb tcpip <port>
  ```
- **Connect to ADB server:**
  ```bash
  adb connect <device_ip>
  ```
- **Restart the ADB daemon listening on USB:**
  ```bash
  adb usb
  ```

## 2. Device Reboot Options
- **Reboot the device:**
  ```bash
  adb reboot
  ```
- **Reboot into recovery mode:**
  ```bash
  adb reboot recovery
  ```
- **Reboot into bootloader mode:**
  ```bash
  adb reboot bootloader
  ```

## 3. Device Information & Management
- **Get device properties:**
  ```bash
  adb shell getprop
  ```
- **Get device state:**
  ```bash
  adb get-state
  ```
- **Print serial number:**
  ```bash
  adb get-serialno
  ```
- **Get battery status:**
  ```bash
  adb shell dumpsys battery
  ```
- **Get Wi-Fi IP:**
  ```bash
  adb shell ip -f inet addr show wlan0
  ```
- **Check system uptime:**
  ```bash
  adb shell uptime
  ```
- **Get disk space info:**
  ```bash
  adb shell df
  ```
- **Get device model:**
  ```bash
  adb shell getprop ro.product.model
  ```

## 4. File Operations
- **Push a file to the device:**
  ```bash
  adb push <local-path> <remote-path>
  ```
- **Pull a file from the device:**
  ```bash
  adb pull <remote-path> <local-path>
  ```
- **List files on the device:**
  ```bash
  adb shell ls <directory-path>
  ```
- **Copy files between directories:**
  ```bash
  adb shell cp <source-path> <destination-path>
  ```
- **Move files:**
  ```bash
  adb shell mv <source-path> <destination-path>
  ```

## 5. App Management
- **Install APK:**
  ```bash
  adb install <apk-file>
  ```
- **Install APK and keep all its data:**
  ```bash
  adb install -r <apk-file>
  ```
- **Uninstall APK:**
  ```bash
  adb uninstall <package-name>
  ```
- **List installed packages:**
  ```bash
  adb shell pm list packages
  ```
- **Clear app data:**
  ```bash
  adb shell pm clear <package-name>
  ```
- **Launch an app:**
  ```bash
  adb shell am start -n <package-name>/<activity-name>
  ```
- **Stop a running app:**
  ```bash
  adb shell am force-stop <package-name>
  ```

## 6. Shell Commands
- **Access the shell:**
  ```bash
  adb shell
  ```
- **Run a command:**
  ```bash
  adb shell <command>
  ```
- **List running processes:**
  ```bash
  adb shell ps
  ```
- **Check CPU usage:**
  ```bash
  adb shell top
  ```
- **Check memory usage:**
  ```bash
  adb shell dumpsys meminfo
  ```

## 7. Debugging
- **View logs:**
  ```bash
  adb logcat
  ```
- **Filter logs by tag:**
  ```bash
  adb logcat -s <tag>
  ```
- **Save log to a file:**
  ```bash
  adb logcat -f <filename>
  ```
- **Clear log:**
  ```bash
  adb logcat -c
  ```
- **Dump system logs:**
  ```bash
  adb bugreport
  ```
- **Record screen:**
  ```bash
  adb shell screenrecord /sdcard/record.mp4
  ```

## 8. Root and System Management
- **Switch to root:**
  ```bash
  adb root
  ```
- **Remount filesystem with read/write access:**
  ```bash
  adb remount
  ```
- **Access root shell:**
  ```bash
  adb shell su
  ```

## 9. Fastboot Commands
- **Flash boot image:**
  ```bash
  fastboot flash boot <boot.img>
  ```
- **Flash recovery image:**
  ```bash
  fastboot flash recovery <recovery.img>
  ```
- **Flash system image:**
  ```bash
  fastboot flash system <system.img>
  ```
- **Unlock bootloader:**
  ```bash
  fastboot oem unlock
  ```
- **Lock bootloader:**
  ```bash
  fastboot oem lock
  ```

## 10. Network and Wireless
- **Connect device via TCP/IP:**
  ```bash
  adb tcpip 5555
  ```
- **Connect device wirelessly:**
  ```bash
  adb connect <device-ip>:5555
  ```
- **Disconnect wireless ADB:**
  ```bash
  adb disconnect <device-ip>:5555
  ```

## 11. Advanced Commands
- **Enable USB debugging:**
  ```bash
  adb shell settings put global development_settings_enabled 1
  ```
- **Take a screenshot:**
  ```bash
  adb exec-out screencap -p > screenshot.png
  ```
- **Simulate input key event:**
  ```bash
  adb shell input keyevent <key-code>
  ```
- **Simulate tap event:**
  ```bash
  adb shell input tap <x> <y>
  ```
- **Simulate swipe gesture:**
  ```bash
  adb shell input swipe <x1> <y1> <x2> <y2> <duration>
  ```

## 12. Additional Useful Commands
- **Backup Device:**
  ```bash
  adb backup -all
  ```
- **Restore Device:**
  ```bash
  adb restore /path/to/backupfile.ab
  ```
- **Set device date:**
  ```bash
  adb shell date MMDDYYYY.XX
  ```
- **Open settings for a specific app:**
  ```bash
  adb shell am start -a android.settings.APPLICATION_DETAILS_SETTINGS -d package:<com.package.example>
  ```
- **Auto rotate settings:**
  ```bash
  adb shell content insert --uri content://settings/system --bind name:s:accelerometer_rotation --bind value:i:1  # Enable
  adb shell content insert --uri content://settings/system --bind name:s:accelerometer_rotation --bind value:i:0  # Disable
  ```

## 13. Logcat Options
- **Default options:**
  - V — Verbose
  - D — Debug
  - I — Info
  - W — Warning
  - E — Error
  - F — Fatal
  - S — Silent

- **Example logcat commands:**
  - Display all log messages:
    ```bash
    adb logcat *:V
    ```
  - Clear the log buffer:
    ```bash
    adb logcat -c
    ```
  - Display log with timestamps:
    ```bash
    adb logcat -v time
    ```

## 14. Dumpsys Commands
- **List all active services:**
  ```bash
  adb shell dumpsys -l
  ```
- **Show battery stats:**
  ```bash
  adb shell dumpsys battery
  ```
- **Display network stats:**
  ```bash
  adb shell dumpsys netstats
  ```

## 15. Tips & Tricks
- **Check how many notifications you have:**
  ```bash
  adb shell dumpsys notification | grep NotificationRecord | wc -l
  ```
- **Simulate swipe down for notifications:**
  ```bash
  adb shell input swipe 0 0 0 300
  ```
