# Step 3: Set up your Viam Rover
Here, you'll finish setting up the Rover's power source, set the low voltage cutoff circuit, and mount the Raspberry Pi onto the motherboard.

## Add the power supply
The Viam Rover 2 arrives with the 18650 battery pack wired into the power input terminal block. The battery pack works with batteries 67.5 mm in length, but the battery housing includes a spring to accommodate most batteries of that approximate length.

1. Turn the rover over so that you can see the battery housing.

    <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/rover-underview.png" resize="400x" declaredimensions=true alt="Under view of rover with battery pack." />

1. Place four 18650 batteries (taking care to ensure correct polarity orientation) inside the battery pack to provide power to the rover, which can be turned on and off through the power switch.


> 💡 Ensure that the batteries are making contact with the terminals inside the battery pack. Some shorter batteries might need to be pushed along to ensure that contact is being made.

### Configure the low voltage cutoff circuit

Now that you have connected your power supply to your rover, you need to configure the low voltage cutoff circuit.
You must configure two settings:

1.  The low voltage cutoff
2.  The reconnect voltage

The reconnect voltage is the voltage increment above the cutoff point that is needed for the power to reconnect. The nominal voltage is 14.8V, so you should set the low voltage threshold to 14.7.
You can adjust this value if using a battery that has an alternative nominal voltage.

To set the low voltage cutoff and reconnect voltage:

1.  Turn on the circuit using the switch.
    The LED indicator should indicate a current voltage level of 14.8-16V depending on the battery charge status:

     <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/circuit-led.png" resize="300x" declaredimensions=true alt="LED with voltage level displayed on low voltage cutoff circuit" />

2.  Hold down the left button until the LED display starts flashing with the low cutoff value.
    The factory default low cutoff value is 12V.
3.  Use the left (+) and right (-) buttons to set the voltage to 14.7V (or whatever you want the cutoff to be).
4.  Wait for the indicator to stop flashing.
5.  Hold down the right button until the LED display starts flashing with the reconnect voltage value. The factory default reconnect voltage is 2.0V.
6.  Use the left (+) and right (-) buttons to set the reconnect voltage to 0.2V.
7.  Wait for the indicator to stop flashing.

Your voltage cutoff circuit is now configured.
When the voltage drops below 14.8V (or reaches the cutoff point you chose), a relay will disconnect the motherboard.
A minimum voltage of 14.9V will be needed to reconnect the power (that is, after charging the batteries).

### Connect the ribbon cable, Pi, and camera

1. To attach the Raspberry Pi, first unscrew the top of the rover with the biggest Allen key.
1. Then use the smallest Allen key and the provided M2.5 screws to attach the Raspberry Pi to your rover through the standoffs on the motherboard. The Raspberry Pi 4 should be mounted such that the USB ports are to the right, as viewed from above.
 
    <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/ribbon-cable2.png" resize="400x" declaredimensions=true alt="Ribbon cable attached to pi" />

1. Use the ribbon cable to connect the Raspberry Pi 4 to the motherboard.
The ribbon cable comes connected to the motherboard out of the box, wrap it over the top of the Raspberry Pi 4 and connect with the GPIO pins as shown:

    <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/ribbon-cable1.png" resize="400x" declaredimensions=true alt="Ribbon cable attached to pi" />

1. Lastly, connect the webcam's USB lead to any USB port on your Pi.
1. Screw the top plate back on with the biggest Allen key and use the power switch to turn the rover on.
1. Wait a second for the low voltage cutoff relay to trip and provide power to the rover motherboard. If the Pi has power, the lights on the Raspberry Pi will light up.

## Alternative board configurations

This workshop details setup steps using a Raspberry Pi 4, but you can use [different boards](https://docs.viam.com/dev/reference/try-viam/rover-resources/rover-tutorial/#motherboard) with your Viam Rover 2 with some modifications while attaching the boards.

Reference the appropriate alternative hole pattern provided on the motherboard:

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/hole-patterning.png" resize="400x" declaredimensions=true alt="Viam rover 2 motherboard hole patterns" />

Follow your [specific board](https://docs.viam.com/dev/reference/try-viam/rover-resources/rover-tutorial/#alternative-board-configurations)'s modification steps if you decide to configure your rover with a different board than a Raspberry Pi 4.

