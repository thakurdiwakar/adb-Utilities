
# Basic ADB Commands

## Device Connection

- **List connected devices:**
  ```bash
  adb devices
  ```

- **List devices with details:**
  ```bash
  adb devices -l
  ```

## Server Operations

- **Start the ADB server:**
  ```bash
  adb start-server
  ```

- **Kill the ADB server:**
  ```bash
  adb kill-server
  ```

## Device Management

- **Reboot the device:**
  ```bash
  adb reboot
  ```

- **Reboot into bootloader mode:**
  ```bash
  adb reboot bootloader
  ```

- **Reboot into recovery mode:**
  ```bash
  adb reboot recovery
  ```

- **Get device information:**
  ```bash
  adb shell getprop
  ```

- **Check battery status:**
  ```bash
  adb shell dumpsys battery
  ```

## File Operations

- **Push a file to the device:**
  ```bash
  adb push <local-file> <remote-location>
  ```

- **Pull a file from the device:**
  ```bash
  adb pull <remote-file> <local-location>
  ```

## App Management

- **Install an APK:**
  ```bash
  adb install <apk-file>
  ```

- **Uninstall an app:**
  ```bash
  adb uninstall <package-name>
  ```

- **List installed packages:**
  ```bash
  adb shell pm list packages
  ```

- **Launch an app:**
  ```bash
  adb shell am start -n <package>/<activity>
  ```

- **Force stop an app:**
  ```bash
  adb shell am force-stop <package-name>
  ```

## Shell Commands

- **Open a shell on the device:**
  ```bash
  adb shell
  ```

- **Run a command on the device:**
  ```bash
  adb shell <command>
  ```

- **List files in a directory on the device:**
  ```bash
  adb shell ls <directory>
  ```

## Root Permissions

- **Restart ADB with root permissions:**
  ```bash
  adb root
  ```

- **Remount the file system as read/write:**
  ```bash
  adb remount
  ```

- **Switch to root user:**
  ```bash
  adb shell su
  ```

## Fastboot and Verity

- **Disable device verification (might require root):**
  ```bash
  adb disable-verity
  ```

- **Reboot into fastboot mode:**
  ```bash
  adb reboot fastboot
  ```

- **Flash a boot image:**
  ```bash
  fastboot flash boot <boot-image>
  ```

- **Unlock the bootloader:**
  ```bash
  fastboot oem unlock
  ```

- **Lock the bootloader:**
  ```bash
  fastboot oem lock
  ```

## Miscellaneous

- **Get the list of connected devices:**
  ```bash
  adb devices
  ```

- **Show the ADB version:**
  ```bash
  adb version
  ```

- **Update ADB:**
  ```bash
  adb update
  

