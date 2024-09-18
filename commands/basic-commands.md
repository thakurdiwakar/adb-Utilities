

# Basic ADB Commands

## Device Connection & Server Management:
- List connected devices (with details):
  ```bash
  adb devices -l
  ```
- Start the ADB server:
  ```bash
  adb start-server
  ```
- Kill the ADB server:
  ```bash
  adb kill-server
  ```

## Device Reboot Options:
- Reboot the device:
  ```bash
  adb reboot
  ```
- Reboot into bootloader:
  ```bash
  adb reboot bootloader
  ```
- Reboot into recovery:
  ```bash
  adb reboot recovery
  ```
- Reboot into fastboot mode:
  ```bash
  adb reboot fastboot
  ```

## Device Information & Management:
- Get device properties:
  ```bash
  adb shell getprop
  ```
- Get the battery status:
  ```bash
  adb shell dumpsys battery
  ```
- Get the Wi-Fi IP:
  ```bash
  adb shell ip -f inet addr show wlan0
  ```
- Check system uptime:
  ```bash
  adb shell uptime
  ```
- Get disk space info:
  ```bash
  adb shell df
  ```
- Get device serial number:
  ```bash
  adb get-serialno
  ```
- Get device model:
  ```bash
  adb shell getprop ro.product.model
  ```

## File Operations:
- Push a file to the device:
  ```bash
  adb push <local-path> <remote-path>
  ```
- Pull a file from the device:
  ```bash
  adb pull <remote-path> <local-path>
  ```
- List files on the device:
  ```bash
  adb shell ls <directory-path>
  ```
- Copy files between directories:
  ```bash
  adb shell cp <source-path> <destination-path>
  ```
- Move files:
  ```bash
  adb shell mv <source-path> <destination-path>
  ```

## App Management:
- Install APK:
  ```bash
  adb install <apk-file>
  ```
- Uninstall APK:
  ```bash
  adb uninstall <package-name>
  ```
- List installed packages:
  ```bash
  adb shell pm list packages
  ```
- Get package details:
  ```bash
  adb shell dumpsys package <package-name>
  ```
- Clear app data:
  ```bash
  adb shell pm clear <package-name>
  ```
- Launch an app:
  ```bash
  adb shell am start -n <package-name>/<activity-name>
  ```
- Stop a running app:
  ```bash
  adb shell am force-stop <package-name>
  ```

## Shell Commands:
- Access the shell:
  ```bash
  adb shell
  ```
- Run a command:
  ```bash
  adb shell <command>
  ```
- List running processes:
  ```bash
  adb shell ps
  ```
- Check CPU usage:
  ```bash
  adb shell top
  ```
- Check memory usage:
  ```bash
  adb shell dumpsys meminfo
  ```
- Check network usage:
  ```bash
  adb shell dumpsys netstats
  ```

## Debugging:
- View logs:
  ```bash
  adb logcat
  ```
- Filter logs by tag:
  ```bash
  adb logcat -s <tag>
  ```
- Save log to file:
  ```bash
  adb logcat -f <filename>
  ```
- Clear log:
  ```bash
  adb logcat -c
  ```
- Dump system logs:
  ```bash
  adb bugreport
  ```
- Record screen:
  ```bash
  adb shell screenrecord /sdcard/record.mp4
  ```

## Root and System Management:
- Switch to root:
  ```bash
  adb root
  ```
- Remount filesystem with read/write access:
  ```bash
  adb remount
  ```
- Access root shell:
  ```bash
  adb shell su
  ```

## Fastboot Commands:
- Flash boot image:
  ```bash
  fastboot flash boot <boot.img>
  ```
- Flash recovery image:
  ```bash
  fastboot flash recovery <recovery.img>
  ```
- Flash system image:
  ```bash
  fastboot flash system <system.img>
  ```
- Unlock bootloader:
  ```bash
  fastboot oem unlock
  ```
- Lock bootloader:
  ```bash
  fastboot oem lock
  ```

## Network and Wireless:
- Connect device via TCP/IP:
  ```bash
  adb tcpip 5555
  ```
- Connect device wirelessly:
  ```bash
  adb connect <device-ip>:5555
  ```
- Disconnect wireless ADB:
  ```bash
  adb disconnect <device-ip>:5555
  ```

## Advanced Commands:
- Enable USB debugging:
  ```bash
  adb shell settings put global development_settings_enabled 1
  ```
- Take a screenshot:
  ```bash
  adb exec-out screencap -p > screenshot.png
  ```
- Simulate input key event:
  ```bash
  adb shell input keyevent <key-code>
  ```
- Simulate tap event:
  ```bash
  adb shell input tap <x> <y>
  ```
- Simulate swipe gesture:
  ```bash
  adb shell input swipe <x1> <y1> <x2> <y2> <duration>
  ```

