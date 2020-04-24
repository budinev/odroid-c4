#### __Download source:__

```
$ mkdir ~/mydroid
$ cd ~/mydroid
$ repo init -u https://github.com/odroid-dev/android_manifest.git -b android-9.0
$ repo sync -j$(nproc) --no-tags --no-clone-bundle
```

#### __Set up toolchains path:__

```
$ export PATH=$PATH:/PATH/TO/mydroid/vendor/toolchains/gcc-9.x-aarch64-linux-gnu/bin
$ export PATH=$PATH:/PATH/TO/mydroid/vendor/toolchains/gcc-linaro-aarch64-none-elf-4.9-2014.09_linux/bin
$ export PATH=$PATH:/PATH/TO/mydroid/vendor/toolchains/gcc-linaro-arm-none-eabi-4.8-2014.04_linux/bin
```
+ Replace */PATH/TO/* with your current correct path.

#### __Set up ccache:__
+ Only needed if you compile sources more than one time.
```
$ export USE_CCACHE=1
$ export CCACHE_DIR=/path/to/.ccache
$ /usr/bin/ccache -M 50G
```

#### __To build the arm64 variant:__

```
$ export ANDROID_BUILD_TYPE=64
```

#### __To build the Android TV variant:__

```
$ export TARGET_BUILD_GOOGLE_ATV=true
```

#### __Select the target device:__

```
$ source build/envsetup.sh
$ lunch odroid[c4|n2]-[userdebug|eng]
```

#### __Compile Android image:__

```
$ make -j$(nproc)
$ make -j$(nproc) selfinstall
```

#### __For support refer to:__
+ ODROID-N2: https://forum.odroid.com/viewtopic.php?f=178&t=35463
