# Android pentesting

## Install Android-x86 emulated image in VirtualBox

1. Download Android image from [http://www.osboxes.org/android-x86/](http://www.osboxes.org/android-x86/). Version 4.4-r4 is recommended for the rest to work.
1. (Optional) Configure portrait screen orientation using this [step by step instruction](http://stackoverflow.com/questions/6202342/switch-android-x86-screen-resolution/8273560).

## Xposed install in x86 emulator

Download and install Xposed installer but do not run it!
[http://dl-xda.xposed.info/modules/de.robv.android.xposed.installer_v33_36570c.apk](http://dl-xda.xposed.info/modules/de.robv.android.xposed.installer_v33_36570c.apk)

~~~
adb shell
su
mkdir -p /data/data/de.robv.android.xposed.installer/conf/
echo 0x98 > /data/data/de.robv.android.xposed.installer/conf/jit_reset_offset 
chmod 664 /data/data/de.robv.android.xposed.installer/conf/jit_reset_offset
~~~

Now you can run Xposed installer.

## Symlink busybox and su for OS related modules to work

In drozer console run:

~~~
run tools.setup.busybox
~~~

Then in adb shell run:

~~~
su
mv /data/data/com.mwr.dz/bin/busybox /data/data/com.mwr.dz/bin/busybox.dz
ln -s /system/xbin/busybox /data/data/com.mwr.dz/bin/busybox
ln -s /system/bin/su /data/data/com.mwr.dz/su
~~~