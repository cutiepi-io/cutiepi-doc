## System Flashing Guide 

### Download the system image 

Currently there are two variants of system image, both in beta stage: 

- [Raspberry Pi OS with CutiePi shell](https://drive.google.com/file/d/1BfXrdC2TshKuaOj5p7D4a3c6twBfNYid)

        File: raspios-cutiepi-arm64-1215.img.xz (992MB)
        SHA1: ef7d968f74b9313867cf46c839a40d899d957c53

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
