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
- **Check if ADB server is running:**
  ```bash
  adb get-state
  ```
- **Show ADB server version:**
  ```bash
  adb version
  ```
- **List the ADB log level:**
  ```bash
  adb shell getprop log.tag.ADB
  ```
- **Check ADB host connection info:**
  ```bash
  adb host-features
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
- **Reboot into safe mode:**
  ```bash
  adb reboot safe
  ```
- **Reboot into fastboot mode:**
  ```bash
  adb reboot fastboot
  ```
- **Reboot to system image:**
  ```bash
  adb reboot system
  ```
- **Reboot to recovery with a delay:**
  ```bash
  adb shell sleep 5 && adb reboot recovery
  ```
- **Schedule a reboot:**
  ```bash
  adb shell "sleep 60 && reboot"
  ```
- **Reboot and clear cache:**
  ```bash
  adb shell twrp wipe cache
  ```
- **Check last reboot reason:**
  ```bash
  adb shell dumpsys boot | grep reason
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
- **Get Android version:**
  ```bash
  adb shell getprop ro.build.version.release
  ```
- **Get device manufacturer:**
  ```bash
  adb shell getprop ro.product.manufacturer
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
- **Delete a file:**
  ```bash
  adb shell rm <file-path>
  ```
- **Create a directory:**
  ```bash
  adb shell mkdir <directory-path>
  ```
- **Remove a directory:**
  ```bash
  adb shell rmdir <directory-path>
  ```
- **Get file permissions:**
  ```bash
  adb shell ls -l <file-path>
  ```
- **Change file permissions:**
  ```bash
  adb shell chmod <permissions> <file-path>
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
- **Get APK path of installed package:**
  ```bash
  adb shell pm path <package-name>
  ```
- **List permissions for a package:**
  ```bash
  adb shell pm dump <package-name> | grep "permission"
  ```
- **Grant permission to an app:**
  ```bash
  adb shell pm grant <package-name> <permission>
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
- **Run a command as root:**
  ```bash
  adb shell su -c "<command>"
  ```
- **Check active network connections:**
  ```bash
  adb shell netstat
  ```
- **Check disk usage of a directory:**
  ```bash
  adb shell du -sh <directory-path>
  ```
- **Get environment variables:**
  ```bash
  adb shell printenv
  ```
- **Run a command in the background:**
  ```bash
  adb shell "<command> &"
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
- **Capture a bug report:**
  ```bash
  adb shell dumpsys > bugreport.txt
  ```
- **Show logcat buffer sizes:**
  ```bash
  adb logcat -g
  ```
- **Set logcat buffer size:**
  ```bash
  adb logcat -b all -G <size>
  ```
- **Monitor logcat in real-time:**
  ```bash
  adb logcat -v time | grep <tag>
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
- **Change SELinux mode:**
  ```bash
  adb shell setenforce 0  # Permissive mode
  ```
- **Check SELinux status:**
  ```bash
  adb shell getenforce
  ```
- **Enable system features:**
  ```bash
  adb shell settings put global <setting> <value>
  ```
- **Disable system features:**
  ```bash
  adb shell settings delete global <setting>
  ```
- **List system settings:**
  ```bash
  adb shell settings list global
  ```
- **Backup system app data:**
  ```bash
  adb backup -f backup.ab -apk -shared <package-name>
  ```
- **Restore system app data:**
  ```bash
  adb restore backup.ab
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
- **Get device info:**
  ```bash
  fastboot devices
  ```
- **Reboot into system:**
  ```bash
  fastboot reboot
  ```
- **Reboot into recovery:**
  ```bash
  fastboot reboot recovery
  ```
- **Erase a partition:**
  ```bash
  fastboot erase <partition>
  ```
- **Check bootloader status:**
  ```bash
  fastboot getvar unlocked
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
- **Ping a device:**
  ```bash
  adb shell ping -c 4 <device-ip>
  ```
- **Check Wi-Fi status:**
  ```bash
  adb shell dumpsys wifi | grep "Wi-Fi is"
  ```
- **Enable Wi-Fi:**
  ```bash
  adb shell svc wifi enable
  ```
- **Disable Wi-Fi:**
  ```bash
  adb shell svc wifi disable
  ```
- **Get current IP address:**
  ```bash
  adb shell ip addr show wlan0
  ```
- **Scan for available Wi-Fi networks:**
  ```bash
  adb shell dumpsys wifi | grep "SSID"
  ```
- **Connect to a Wi-Fi network:**
  ```bash
  adb shell am start -n com.android.settings/.wifi.WifiSettings
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
- **Change screen orientation:**
  ```bash
  adb shell settings put system user_rotation <0|1|2|3>
  ```
- **Toggle airplane mode:**
  ```bash
  adb shell settings put global airplane_mode_on 1
  adb shell am broadcast -a android.intent.action.AIRPLANE_MODE
  ```
- **Toggle do not disturb:**
  ```bash
  adb shell settings put global zen_mode <mode>
  ```
- **Get device logs for specific app:**
  ```bash
  adb logcat | grep <package-name>
  ```
- **Find a specific string in logs:**
  ```bash
  adb logcat | grep "<string>"
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
- **Check device logs:**
  ```bash
  adb logcat -d
  ```
- **Get current user:**
  ```bash
  adb shell whoami
  ```
- **Open app settings directly:**
  ```bash
  adb shell am start -n <package-name>/.<activity-name>
  ```
- **Get last 100 lines of logcat:**
  ```bash
  adb logcat -d | tail -n 100
  ```
- **Check system properties:**
  ```bash
  adb shell getprop
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
- **Show running services:**
  ```bash
  adb shell dumpsys activity services
  ```
- **Get memory usage of an app:**
  ```bash
  adb shell dumpsys meminfo <package-name>
  ```
- **Display CPU usage:**
  ```bash
  adb shell dumpsys cpuinfo
  ```
- **List all providers:**
  ```bash
  adb shell dumpsys content providers
  ```
- **Show current activity:**
  ```bash
  adb shell dumpsys activity | grep "mResumedActivity"
  ```
- **Display current settings:**
  ```bash
  adb shell dumpsys settings
  ```
- **Get foreground app:**
  ```bash
  adb shell dumpsys activity | grep "mCurrentFocus"
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
- **Get current foreground app:**
  ```bash
  adb shell dumpsys activity | grep "mResumedActivity"
  ```
- **Take a video recording of the screen:**
  ```bash
  adb shell screenrecord /sdcard/video.mp4
  ```
- **Get a list of all permissions:**
  ```bash
  adb shell pm list permissions
  ```
- **Get device temperature:**
  ```bash
  adb shell dumpsys battery | grep temperature
  ```
- **List all Bluetooth devices:**
  ```bash
  adb shell dumpsys bluetooth_manager
  ```
- **Check SIM card status:**
  ```bash
  adb shell dumpsys telephony.registry | grep "mServiceState"
  ```
- **Get build properties:**
  ```bash
  adb shell getprop | grep "ro."
  ```
- **Get list of running apps:**
  ```bash
  adb shell dumpsys activity | grep "Running activities"
  ```

