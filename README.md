# Configuring-RaspberryPi
Setting Up a Raspberry Pi and Configuring Customizable User Settings



## Raspberry Pi Set Up Instructions

**Assembling a Pi**

-   [Video tutorial](https://www.youtube.com/watch?v=XKVd5638T_8). Missing a couple of steps, like heatsink and camera install, but good overview of the process

-   Slot the micro-SD card into the back of the pi

-   Install heat-sinks onto the pi

-   Insert a long ribbon cable (\>24”) into the camera port on the pi

-   Add a short ribbon cable (\~6”) to the back of the touch screen if there isn’t one already

-   Install the touchscreen into the case, with the ribbon cable fed through the back

-   Install the pi into the case, and attach the ribbon cable from the touchscreen to the display port of the pi

-   Plug the power splitter into the ports below the pi and touchscreen

-   Plug the power supply into the female port on the power splitter



**Burning the SD card**

-   Install Raspberry Pi OS using [Raspberry Pi imager](https://www.raspberrypi.com/software/)

    -   Under “Choose Device” select Raspberry Pi 4

    -   Under “Operating System” scroll to Raspberry Pi OS (other) and select Raspberry Pi OS (Legacy, 64-bit)

    -   Under “Storage” select your microSD card

-   A popup window will appear asking if you want to customize your pi’s OS, select yes

    -   Check “Set a Hostname” – this can be anything but can only contain letters, numbers, or underscores

        -   Ex. Hostname: train_with_shain

    -   Check “Set username and password” – this is important for SSH capabilities and preventing security bugs

        -   Username will become the name of your main directory in the pi (same as setting up a computer user profile)

        -   Send me your username and password when finished so I can SSH into the pi

    -   Check “Configure wireless LAN”

        -   SSID is the name of your WiFi

        -   Password is your WiFi password

    -   Check “Set locale setting”

        -   Set time zone to US and keyboard layout to standard US or whatever you prefer 

    -   In the top menu bar, navigate to the OPTIONS pane and check “Eject media when finished” and “Enable telemetry”

    -   Click SAVE at the bottom of the pane, then click Yes to apply OS customization settings in the popup, and select Yes again to begin writing the Pi OS onto the microSD card

-   When finished, eject the microSD card safely from your computer and insert it into the SD slot on the Pi’s main motherboard

-   Plug the splitter cable into both USBC ports located at the bottom of the pi and near the adjustable hinge of the LCD case

-   Plug USBC side of the power cable into the splitter USBC cable and then plug the power cable into the wall. Make sure the pi turns on (red light on the pi’s motherboard) and the LCD screen turns on

 

**Configuring Custom User Functionalities**

-   In the top left tool bar of the main screen, click on the black terminal window icon

-   Plug a keyboard into one of the USB ports on the Pi

-   In the terminal window, type:

```{bash}
sudo raspi-config
```

-   Locate the “Hostname” option and make sure the correct hostname is displayed. This should be the same hostname you chose when setting up the Pi OS

-   Ensure ssh is enabled. To do this, navigate to “interface options” within the configuration menu, choose “SSH,” then accept the security risk warning by selecting enable

-   Enable camera/sensor capabilities. Navigate back to “interface options” in the pi configuration window, select the option to enable pi camera, then click enable

-   Exit the configuration window and reboot the pi by typing the following in the terminal window:

```{bash}
sudo reboot
```

-   Once the pi is rebooted, open the terminal application again and type:

```{bash}
ifconfig
```

-   Record the MAC address associated with the eth0 port and the IP address

    -   The IP address can also be identified by touching the WiFi icon in the top toolbar of the main pi window homepage twice

    -   Send me a screen shot or picture of the ifconfig output containing the MAC address and IP



**Setting Up and Testing the pi camera**

-   Insert a long ribbon cable (\>2ft) into the camera port on the pi (this is the second ribbon cable port on the Pi's motherboard)

-   Insert the other end of the long ribbon cable into the port on the back of the pi camera (the V2.1 raspi cam - not the autofocus one)

-   Open the terminal application

-   Start a python session by typing:

```{bash}
python3
```

-   Import picamera by running the following three lines of code:

```{bash}
import picamera
cam = picamera.PiCamera()
cam.start_preview()
```

-   After running the last line, the Pi screen should change to the camera view
