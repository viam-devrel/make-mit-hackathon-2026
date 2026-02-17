# Step 4: Create a Viam machine

## Create a Viam machine
1. In [the Viam app](https://app.viam.com/fleet/locations) under the **LOCATIONS** tab, create a machine by typing in a name and clicking **Add machine**. (If you don't have any location, you may need to create one first before you can create a machine.)

## Install `viam-server` onto your Pi


1. Click **View setup instructions**.
    ![view setup instructions](assets/setupInstructions.png)
1. Install `viam-server` on the Raspberry Pi device that you want to use to communicate with and control your rover. Select the `Linux / Aarch64` platform for the Raspberry Pi to control the rover, and leave your installation method as [`viam-agent`](https://docs.viam.com/how-tos/provision-setup/#install-viam-agent).
   ![select platform](assets/selectPlatform.png)
1. Use the `viam-agent` to download and install `viam-server` on your Raspberry Pi. Follow the instructions to run the command provided in the setup instructions from the SSH prompt of your Raspberry Pi.
   ![SSH and install viam server](assets/installViamServer.png)
1. The setup page will indicate when the machine is successfully connected.
    ![machine successfully connected](assets/machineConnected.png)