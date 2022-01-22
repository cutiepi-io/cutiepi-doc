## OS Porting Guide 

## How to rebuild the CutiePi image

The prebuilt images are generated using the official tool [pi-gen](https://github.com/RPi-Distro/pi-gen), you can find the needed files for CutiePi here [https://github.com/cutiepi-io/pi-gen_stage4.5-cutiepi](https://github.com/cutiepi-io/pi-gen_stage4.5-cutiepi) 

The build instructions is in the repository's README file. 

## Porting 

This a detailed Raspberry Pi OS change list that includes all the modifications we've made into the system image. 

Please use it as a reference for porting other OSes onto the CutiePi tablet. 

### Drivers 

The needed display driver and overlay has been merged into Raspberry Pi's official linux tree (rpi-5.10.y branch). We kept the driver and overlay files in the [cutiepi-drivers](https://github.com/cutiepi-io/cutiepi-drivers) repo for reference. 

Two device tree overlays (for display, and gyro) needed: 

    /boot/overlays/cutiepi-panel.dtbo
    /boot/overlays/mpu6050-i2c5.dtbo

### `/boot/config.txt`

    [cm4]
    # use full kms 
    dtoverlay=vc4-kms-v3d

    arm_64bit=1
    otg_mode=1
    avoid_warnings=2

    # for display 
    dtparam=i2c_arm=on
    dtoverlay=cutiepi-panel

    # for MCU
    enable_uart=1
    dtoverlay=uart1

    # for gyro 
    dtoverlay=i2c5,pins_10_11
    dtoverlay=mpu6050-i2c5,interrupt=27

    # for camera 
    start_x=1
    gpu_mem=128
    dtoverlay=ov5647

### `/boot/cmdline.txt`

The parameter `console=ttyS0,115200` was removed in order to enable MCU UART reading. 

### Packages 

Following packages has been preinstalled in the image: 

    sudo apt install cmst connman neofetch cpufrequtils iio-sensor-proxy \
    libqt5serialport5 libqt5multimedia5-plugins qml-module-qt-labs-folderlistmodel \
    qml-module-qt-labs-platform qml-module-qt-labs-settings qml-module-qtgraphicaleffects \
    qml-module-qtmultimedia qml-module-qtquick-controls2 qml-module-qtquick-layouts \
    qml-module-qtquick-localstorage qml-module-qtquick-templates2 qml-module-qtquick-window2 \
    qml-module-qtquick2 qml-module-qtwebengine qml-module-qtquick-virtualkeyboard \
    libqt5hunspellinputmethod5 qtvirtualkeyboard-plugin libqt5virtualkeyboard5

### User configuration 

    sudo gpasswd -a pi render
    sudo gpasswd -a pi dialout
    sudo gpasswd -a pi input

### System configuration 

A binary [cutoff](https://github.com/cutiepi-io/cutiepi-middleware/tree/master/cutoff) was added so systemd cuts the power while executing the actual system halt/poweroff: 

    /usr/lib/systemd/system-shutdown/cutoff 

A [udev rule](https://github.com/cutiepi-io/pi-gen_stage4.5-cutiepi/blob/main/stage4.5-cutiepi/01-tweaks/files/backlight.rules) was added to grant backlight brightness setting permission: 

    /etc/udev/rules.d/backlight.rules

And some configurations: 

    # Changed parameter to work with connman (the connection mananger) 
    /lib/systemd/system/wpa_supplicant.service 

    # this was removed: 
    /etc/wpa_supplicant/wpa_supplicant.conf

    # changed default value 
    /etc/security/limits.conf
    /etc/sysctl.conf

### Desktop integration 

The [cutiepi-mcuproxy](https://github.com/cutiepi-io/cutiepi-middleware/tree/master/mcu-proxy) and the [cutiepi-shell](https://github.com/cutiepi-io/cutiepi-shell/tree/master/app) launcher were added: 

    # binary 
    /usr/local/bin/cutiepi-shell
    /usr/local/bin/cutiepi-mcuproxy

    # autostart desktop files
    /etc/xdg/autostart/cutiepi-shell.desktop
    /etc/xdg/autostart/cutiepi-mcuproxy.desktop

And some configurations: 

    # disable dimming 
    /etc/xdg/lxsession/LXDE-pi/autostart 

    # remove trash bin 
    /etc/xdg/pcmanfm/LXDE-pi/desktop-items-0.conf

### QML libraries 

Following QML libraries ([libconnman-qt](https://git.sailfishos.org/mer-core/libconnman-qt), [nemo-qml-plugin-dbus](https://github.com/sailfishos/nemo-qml-plugin-dbus.git), [yat](https://github.com/jorgen/yat), and [process](https://github.com/cutiepi-io/cutiepi-middleware/tree/master/process)) were added: 

    # For connection manager
    /usr/lib/aarch64-linux-gnu/libconnman-qt5.so* 
    /usr/lib/aarch64-linux-gnu/qt5/qml/MeeGo/Connman/

    # For DBus 
    /usr/lib/aarch64-linux-gnu/libnemodbus.so*
    /usr/lib/aarch64-linux-gnu/qt5/qml/Nemo/DBus/

    # For system command 
    /usr/lib/aarch64-linux-gnu/qt5/qml/Process/

    # For the terminal emulator 
    /usr/lib/aarch64-linux-gnu/qt5/qml/Yat/

### CutiePi shell  

The [cutiepi-shell](https://github.com/cutiepi-io/cutiepi-shell/blob/master/opt/cutiepi-shell) folder, along with other configurations, was added: 

    # CutiePi shell 
    /opt/cutiepi-shell 

    # default wallpaper
    /usr/share/rpd-wallpaper/boombox.png
    /usr/share/rpd-wallpaper/cutiepi*.png
