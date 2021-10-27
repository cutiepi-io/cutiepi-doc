## OS Porting Guide 

This a detailed Raspberry Pi OS change list that includes all the modifications we've made into the system image. 

Please use it as a reference for porting other OSes onto CutiePi tablet. 

### Drivers 

You may find all the drivers and overlays in the [cutiepi-drivers](https://github.com/cutiepi-io/cutiepi-drivers) repo, the most important one is `panel-nwe080`, an out-of-tree kernel driver for the MIPI DSI display. 

We've packed it as a DKMS package and preinstalled under:

    /usr/src/panel-nwe080-1.0 

### `/boot/config.txt`

    # SPI needs to be commented out 
    #dtparam=spi=on 

    [i4]
    # USB host mode
    dtoverlay=dwc2,dr_mode=host

    # WiFi 
    dtparam=ant1

    # graphic
    dtoverlay=vc4-kms-v3d-pi4

    # MIPI DSI display 
    dtoverlay=panel-nwe080

    # touch screen
    dtoverlay=i2c6
    dtoverlay=cutiepi_touch

    # MCU reading (ttyS0)
    enable_uart=1
    dtoverlay=uart1

    # Gyroscope 
    dtoverlay=i2c5,pins_10_11

    # Camera (with dt-blob.bin)
    start_x=1
    gpu_mem=128

### `/boot/cmdline.txt`

The parameter `console=ttyS0,115200` was removed in order to enable MCU UART reading. 

### Packages 

Following packages has been preinstalled in the image: 

    sudo apt install cmst connman neofetch cpufrequtils dkms \
        raspberrypi-kernel-headers cmake clang libpulse-mainloop-glib0 

### User configuration 

	sudo gpasswd -a pi render
    sudo gpasswd -a pi dialout

# Desktop integration 

A binary [cutoff](https://github.com/cutiepi-io/cutiepi-middleware/tree/master/cutoff) was added so systemd cuts the power before executing the actual system halt/poweroff: 

    /usr/lib/systemd/system-shutdown/cutoff 

Following helper scripts and the [systray](https://github.com/cutiepi-io/cutiepi-shell/tree/master/systray) implementation were added: 

    /usr/local/bin/cutiepi-systray

    # screen rotation script using xrandr 
    /usr/local/bin/rotate-screen

    # script for setting default UI 
    /usr/local/bin/set-cutiepi-shell-default.sh
    /usr/local/bin/set-lightdm-default.sh

    /usr/local/bin/start-cutiepi-systray.sh
    /usr/local/bin/start-lightdm.sh

    /etc/xdg/autostart/cutiepi-systray.desktop

And some configurations

    # disable dimming 
    /etc/xdg/lxsession/LXDE-pi/autostart 

    # remove trash bin 
    /etc/xdg/pcmanfm/LXDE-pi/desktop-items-0.conf

    /etc/security/limits.conf
    /etc/sysctl.conf

### CutiePi shell  

    # add /usr/local/lib/aarch64-linux-gnu/ and /opt/qt5/lib
    /etc/ld.so.conf.d/libc.conf

    /lib/systemd/system/wpa_supplicant.service 

    # this is removed: 
    /etc/wpa_supplicant/wpa_supplicant.conf
    
    # prebuilt Qt5.15.2
    /opt/qt5 

    # CutiePi shell 
    /opt/cutiepi-shell 

    # default wallpaper
    /usr/share/rpd-wallpaper/boombox.png
    /usr/share/rpd-wallpaper/cutiepi*.png

    /lib/systemd/system/cutiepi-shell.service

### libcamera 

    /usr/local/share/libcamera/
    /usr/local/libexec/libcamera/
    /usr/local/lib/aarch64-linux-gnu/libcamera*
    # copy from /usr/local/lib/aarch64-linux-gnu/gstreamer-1.0/libgstlibcamera.so
    /usr/lib/aarch64-linux-gnu/gstreamer-1.0/libgstlibcamera.so 