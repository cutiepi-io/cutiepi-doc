# CutiePi tablet - User Manual

CutiePi tablet is a 100% open source Raspberry Pi 4 tablet powered by the Compute Module 4. It has a 5000mAh li-po battery, an 8 inch multi-touch display with 1280 x 800 resolution, and a handle that also doubles as a stand.

The tablet also has a built-in gyroscope, a rear-view camera, a microphone and a speaker, you can simply carry or use it like your everyday gadgets.

## Before You Begin 

- Charge your CutiePi after unboxing - Make sure you're using a regular `5V 3A` power supply, as some fast charger for phones might not work
- Update your SD card - Follow the [System Flasing Guide](https://github.com/cutiepi-io/cutiepi-doc/blob/main/SystemFlashingGuide.md) to download and flash the latest system

## Need Any Help? 

- [Telegram group chat](https://t.me/cutiepi_io) - For community, support, or software related questions
- Mail to [hello@cutiepi.io](mailto:hello@cutiepi.io) - For any non-software related questions

## How to Get Started

![](screenshots/cutiepi-manual-instruction.png)

### Turning CutiePi On / Off

- Power On: Press and hold for `3s` till the backlight turns on, release the power button 
- Sleep/Wake: Short press on the power button 
- Force Shutdown: Press and hold the power button for `10s` till the backlight turns off 

When in doubt of the hardware status, we recommend to do the power cycle: force shutdown (press and hold for 10s), release, then power on. 

### Mind the Heat 

Do not be alarmed if the back of the CutiePi gets hot: 

- This is by design. This means that the heat sink is doing its job 
- If you wish, you may cool down CutiePi by by adjusting the `Power Mode` in the Settings

### In Case of Software Upgrade 

Just like Raspberry Pi, the CutiePi's OS runs on a micro SD card: 

- The SD card slot is located in the lower right corner of the device 
- It is spring loaded, and can be released with a gentle push 
- Insert the card face down 

You can find the latest image download link in the [System Flashing](SystemFlashingGuide.md) guide. 

## The User Interface 

CutiePi shell, our mobile UI powered by the open source Qt framework, turns Raspberry Pi OS into a functional tablet UX. It has most basic functions: 

| Feature | Description |
| ------------- | ------------- |
| ![](screenshots/lockscreen.png) | Lockscreen, swipe from bottom to top to unlock the screen. You can change the wallpaper in `Settings`. | 
| ![](screenshots/system-status.png) | Show the system status by tapping at the upper right corner, you can control the audio volume, orientation lock, system brightness and wifi here.| 
| ![](screenshots/virtualkeyboard.png) | Tap on any input field in the shell will bring up the virtual keyboard. Tap on the "🌐" icon at the bottom left will bring up the language selector.|
| ![](screenshots/webbrowser-url.png) | Typing in the URL bar will bring up the history view. | 
| ![](screenshots/tab-view.png) | Tap on the upper left corner "☰" icon will open the side tabs view. You can open/close tab or switch to different tabs here. |
| ![](screenshots/new-tab.png) | Long press on "➕ New Tab" will open up a terminal emulator tab. A termanl layout keyboard will show up accordingly. | 
| ![](screenshots/settings.png) | The Settings view gives you more controls over the system, for example airplane mode, timezone, and power mode. | 
| ![](screenshots/desktop-toggle.png) |  You can click on the "Switch to Desktop now" button (or the right arrow in system status area) to toggle between shell or desktop UI. |
| ![](screenshots/power-off.png) |  Press and hold the power button for 6s to bring up this power off view. Press and hold for 10s to force shutdown. |

If you wish to customize your own system, or to port other OSes onto CutiePi, please check the [OS Porting Guide](https://github.com/cutiepi-io/cutiepi-doc/blob/main/OSPortingGuide.md). 

## Project Structure

CutiePi tablet is a 100% open source hardware. 
To customize a component or report an isssue, please find the corresponding repository on Github: 

- Hardware - [CutiePi board](https://github.com/cutiepi-io/cutiepi-board) 
- Enclosure - [CutiePi enclosure](https://github.com/cutiepi-io/cutiepi-enclosure)
- Firmware - [CutiePi firmware](https://github.com/cutiepi-io/cutiepi-firmware)
- Drivers - [CutiePi drivers](https://github.com/cutiepi-io/cutiepi-drivers) (already upstreamed, kept for reference) 
- Middleware - [CutiePi middleware](https://github.com/cutiepi-io/cutiepi-middleware)
- User Interface - [CutiePi shell](https://github.com/cutiepi-io/cutiepi-shell) 
- Build system - [pi-gen stage4.5](https://github.com/cutiepi-io/pi-gen_stage4.5-cutiepi) 

## About Warranty

We expect and even encourage you to experiment with the software and hardware. With that said, please keep in mind that the device is under standard warranty. This means breaking components during disassembly will void your warranty.

Please refer to the [Hardware Maintenance](HardwareMaintenanceGuide.md) guide for more information.

### FCC Compliance 

- Name: CutiePi tablet
- Model: `CUTIEPI-01`
- FCC ID: `2A3SP-CUTIEPI-01`

This device complies with part 15 of the FCC Rules. Operation is subject to the condition that this device does not cause harmful interference (1) this device may not cause harmful interference, and (2) this device must accept any interference received, including interference that may cause undesired operation. Any changes or modifications not expressly approved by the party responsible for compliance could void the user's authority to operate the equipment.