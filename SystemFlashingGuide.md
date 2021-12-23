## System Flashing Guide 

### Download the system image 

Currently there are two variants of system image for CutiePi tablet, both in beta: 

- [Raspberry Pi OS arm64 bullseye + CutiePi shell](https://github.com/cutiepi-io/pi-gen_stage4.5-cutiepi/releases/tag/2021-12-21)

        File: raspios-cutiepi-arm64-1221.zip (1.2G)
        SHA1: 53679a4098283d3c31f0fb2a739134169c1cf908

- [Ubuntu Desktop 21.04](https://drive.google.com/file/d/1FnndGdWcw_qGXAdusFi8fYCWpVzwp3ci)

        File: ubuntu-cutiepi-base-arm64-1101.img.xz (1.8G) 
        SHA1: de51282e1f735db056825cf210b638d035b93a2a
        
### Download the image writer 

We recommend using Pi Imager or Etcher: 

- [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- [Etcher](https://www.balena.io/etcher/)

### Flash the micro SD card 

Select the OS image, and click `Write`. 

![](screenshots/flashing.png)

When it's done, insert the card back to CutiePi tablet with the card facing down. 
