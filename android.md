# Android

## Add ADB to path

```shell
# Linux
export PATH=${PATH}:~/Android/Sdk/platform-tools/

# macOS
export PATH=${PATH}:~/Library/Android/sdk/platform-tools/
```

## Check ADB public key fingerprint

```shell
adb pubkey ~/.android/adbkey | awk '{ print $1 }' | openssl base64 -A -a -d | openssl md5 -c | tr a-z A-Z
```

## Cross-compilation of C code

```shell
# Export NDK path (Linux)
export ANDROID_NDK=${HOME}/Android/sdk/ndk/<NDK_VERSION>/
# Set NDK path (macOS)
export ANDROID_NDK=${HOME}/Library/Android/sdk/ndk/<NDK_VERSION>/
# Configure CMake with Android settings
cmake -DANDROID_ABI=arm64-v8a                                                   \
      -DANDROID_PLATFORM=android-28                                             \
      -DCMAKE_TOOLCHAIN_FILE=${ANDROID_NDK}/build/cmake/android.toolchain.cmake \
      ..
# Usual compilation process
make
```

## List connected devices

```shell
# List devices
adb devices
```

## Interract with device

```shell
# Push file to device
adb push <FILE> /data/local/tmp

# Access to device shell
adb shell

# Run command remotely
adb shell <COMMAND>
```
