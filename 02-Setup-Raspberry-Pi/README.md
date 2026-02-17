# Step 2: Setup your Raspbery Pi

**The Viam team should have preflashed microSD cards for you to use. If not, then you can follow the steps below to manually flash and prepare your Raspberry Pi.**

The Raspberry Pi that you'll use with the Viam Rover boots from a microSD card. In this step, you'll flash a microSD card with the Raspberry Pi OS and enable the i2C setting on your Pi. 

1. Connect the microSD card to your computer.
1. Launch the [Raspberry Pi Imager](https://www.raspberrypi.com/software/).
1. In the **Device** step, select your device model.
1. In the **OS** step, select **Raspberry Pi OS (64-bit)** from the menu.
1. In the **Storage** step, choose the micro SD card from the list of devices.
1. To configure your Raspberry Pi for remote access, go through the **Customisation** steps.
1. Set a **Hostname**: enter the name you would like to access the Pi by, for example, `rover`. This will need to be unique among your fellow workshop attendees.
1. Set **Localisation** settings: Set your Capital city to `Los Angeles`, Time zone to `North America/Los Angeles`, and Keyboard layout to `us`.
1. Setup an admin user for your Pi: Enter a **username** (for example, your first name) and **password** that you'll use to log into the Pi. If you skip this step, the default username will be `pi` (not recommended for security reasons). And specify a password.
1. Configure your Pi's Wi-Fi access: Set the **SSID** (Service Set Identifier) AKA your Wi-Fi network name and the **password** (which is the network password). 
1. Enable SSH: In the **Remote Access** step, toggle on the **Enable SSH** is turned on and that **Use password authentication** is selected. This lets you log into your Pi over the network using the username and password you provided earlier. 
   > 💡 Be sure to remember the `hostname`, `username`, and `password` you set, as you will need this when you SSH into your Pi.
1. Click **Next** and skip the **Enable Raspberry Pi Connect** step while leaving the setting turned off. (This lets you link your device to a Raspberry Pi Connect account if you have one; we won't need this)
1. Take a moment to review your choices in the **Summary** step. Once you have confirmed your settings, click **WRITE** to apply your changes to your microSD card. You might also be prompted for permission to erase all data and write to your microSD card. Confirm by clicking `I understand, erase and write`. You may also be prompted by your operating system to enter an administrator password. After granting permissions to the Imager, it will begin writing and then verifying the Linux installation to the microSD card.
1. Remove the microSD card from your computer when the installation is complete.


## Connect with SSH
Now, check and see if you can access your Pi. 

1. Place the microSD card into your Raspberry Pi and boot the Pi by plugging it in to an outlet. A red LED will turn on to indicate that the Pi is connected to power.
1. Once the Pi is started, connect to it with SSH. From a command line terminal window, enter the following command. The text in <> should be replaced (including the < and > symbols themselves) with the user and hostname you configured when you set up your Pi.
   ```bash
   ssh <USERNAME>@<HOSTNAME>.local
   ```
1. If you are prompted “Are you sure you want to continue connecting?”, type “yes” and hit enter. Then, enter the password for your username. You should be greeted by a login message and a command prompt.
1. Update your Raspberry Pi to ensure all the latest packages are installed
   ```bash
   sudo apt update
   sudo apt upgrade
   ```

## Enable communication protocols
You'll need to enable i2C so that your Pi can communicate with the accelerometer and power sensor on your rover.

1. Launch the Pi configuration tool by running the following command
   ```bash
   sudo raspi-config
   ```
1. Use your keyboard to select “Interface Options”, and press return.
   ![raspi config](assets/enablePeriph.png)
1. [Enable the relevant protocols](https://docs.viam.com/installation/prepare/rpi-setup/#enable-communication-protocols) to support our hardware. Enable the I2C protocol on your Pi to get readings from the power sensor anc accelerometer when controlling your rover. Select **I2C** enabled.
   ![enable i2c protocol](assets/i2c.png)
1. Confirm the options to enable the serial login shell and serial interface. And reboot the Pi when you're finished.
   ```bash
   sudo reboot
   ```

### Troubleshooting

#### Write error when imaging Raspberry Pi OS

If you experience the error `Verifying write failed. Contents of SD card is different from what was written to it` when imaging your Raspberry Pi with the Imager in step 5, there might be an issue with your micro SD card reader.

Try a different micro SD card reader, or use a different USB port on your computer.

If you are connecting your SD card reader to your computer through a USB hub, try connecting directly it to your computer instead.

#### Error: can't read from I2C address

If you see the error `error: can't read from I2C address` in your logs after installing `viam-server`, you need to enable `I2C` support on your Raspberry Pi.
You can use the command `sudo journalctl --unit=viam-server` to read through the `viam-server` log file.
Follow the instructions to [enable communication protocols](https://docs.viam.com/operate/reference/prepare/rpi-setup/#enable-communication-protocols) on your Pi to resolve this error.

#### Add additional WiFi credentials

If you move your machine to a different WiFi network, you will have to update the WiFi credentials.

You can update the WiFi configuration by creating a new `wpa_supplicant.conf` file on the "boot" partition.

The steps are explained below.

1. Plug your Pi's microSD card into your computer and create a plain text file called `wpa_supplicant.conf`.

2. Paste the following example into the file, replacing "Name of your wireless LAN" and "Password for your wireless LAN" with your credentials.
   Be sure to use UNIX (LF) line breaks in your text editor.

3. Save the file and eject the microSD card.

4. Put the microSD card back into the Pi and boot the Pi.

The `wpa_supplicant.conf` file will be read by the Pi on boot, and the file will disappear but the WiFi credentials will be updated.

You can duplicate the "network" section to add additional WiFi networks (for example your work, and your home).

The "priority" attribute is optional and can be used to prioritize networks if multiple networks are configured (higher numbers are prioritized).

```bash {class="line-numbers linkable-line-numbers"}
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=us

network={
 ssid="Name of your wireless LAN"
 psk="Password for your wireless LAN"
 priority=10
}

network={
ssid="Name of your other wireless LAN"
psk="Password for your other wireless LAN"
priority=20
}
```