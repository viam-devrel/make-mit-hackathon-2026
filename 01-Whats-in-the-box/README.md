## Step 1: What's inside the box?

Alright hackers, let's make sure your Rover boxes have everything in them. Start opening your Rover kits, finding and taking each of the following items out, and setting them in your workspace:

1. One assembled Viam Rover.

   <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/rover-side.png" resize="400x" declaredimensions=true alt="The side of the assembled Viam Rover"/>

1. Four M2.5 screws for mounting your Raspberry Pi.

   <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover/screws.jpg" resize="200x" declaredimensions=true alt="Four screws" />

1. Two spare stiffer suspension springs.
   You can swap them out with the springs that come with the rover if you need stiffer suspension for higher payload applications.

   <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover/suspension-springs.jpg" resize="200x" declaredimensions=true alt="Two suspension springs" />

1. Three different Allen wrenches (1.5 mm, 2 mm, and 2.5 mm) to unscrew the top and mount the Raspberry Pi.

   <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover/allen-wrenches.png" resize="180x" alt="Three allen wrenches" />

1. Four extenders to increase the height of the rover to house larger internal single-board computers (such as a Jetson Orin Nano).

   <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/extenders.png" resize="400x" declaredimensions=true alt="Four extenders" />

1. Ribbon cable for connecting the Raspberry Pi 4 to the Viam Rover 2 printed circuit board.

   <img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/ribbon-cable.png" resize="400x" declaredimensions=true alt="Ribbon cable" />

## Rover components
Once you confirm you have all of the items in your kit, you can take the top off of the Viam Rover to get a closer look at the different components. These are:

### Dual drive motors with suspension and integrated motor encoders

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover/encoder-motors.jpg" resize="400x" declaredimensions=true alt="two motors with encoders" />

The motors come with integrated encoders.
For information on encoders, see [Encoder Component](https://docs.viam.com/operate/reference/components/encoder/).
For more information on encoded DC motors, see [Encoded Motors](https://docs.viam.com/operate/reference/components/motor/encoded-motor/).

The kit also includes stiffer suspension springs that you can substitute for the ones on the rover.
Generally, a stiff suspension helps with precise steering control.
In contrast, a soft suspension allows the wheels to move up and down to absorb small bumps on the rover's path.

### Motor driver

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover/motor-driver.png" resize="400x" declaredimensions=true alt="A L298N motor driver" />

The kit comes with an L298N driver dual H-Bridge DC motor driver.
L298 is a high voltage and high current motor drive chip, and H-Bridge is typically used to control the rotating direction and speed of DC motors.

### 720p webcam with integrated microphone

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover/webcam.jpg" resize="400x" declaredimensions=true alt="Webcam with cables" />

The webcam that comes with the kit is a standard USB camera device and the rover has a custom camera mount for it.
For more information, see [Camera Component](https://docs.viam.com/operate/reference/components/camera/).

### Motherboard

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/motherboard.png" resize="400x" declaredimensions=true alt="Viam rover 2 motherboard" />

The Viam Rover 2 uses a motherboard to which all ancillary components (buck converter, motor driver, IMU, INA219) are mounted.
This board includes an auxiliary Raspberry Pi 4 pinout that dupont connectors can be connected to, an auxiliary power input terminal, 5V, 3.3V and Ground pins.

The motherboard also incorporates hole patterns for the following alternative single-board computers:

- Jetson Nano and Orin Nano
- Rock Pi S
- Raspberry Pi Zero 2W
- Raspberry Pi 5
- Orange Pi Zero 2

See [Alternative Board Configurations](https://docs.viam.com/dev/reference/try-viam/rover-resources/rover-tutorial/#alternative-board-configurations) for a diagram of this.
Note that these boards require additional parts to be purchased and will not work out of the box with the Viam Rover 2.

### 6DOF IMU

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/mpu6050.png" resize="400x" declaredimensions=true alt="An MPU6050 gyroscope" />

The MPU6050 sensor is a digital 6-axis accelerometer or gyroscope that can read acceleration and angular velocity.
You can access it through the I2C digital interface.
You configure it with Viam on your machine as a [movement sensor](https://docs.viam.com/operate/reference/components/movement-sensor/).

### INA219 power monitoring unit

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/ina219.png" resize="400x" declaredimensions=true alt="An INA219 unit" />

The INA219 unit measures the voltage and current from the power supply.
You can use it to measure battery life status and power consumption.
It connects to the Raspberry Pi 4 through the I2C bus.
You configure it with Viam on your machine as a [power sensor](https://docs.viam.com/operate/reference/components/power-sensor/).

### DC-DC 5V converter

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/buck-converter.png" resize="300x" declaredimensions=true alt="A OKY3502-4 buck converter" />

The DC-to-DC power converter, or, buck converter, steps down voltage from its input to its output.
The OKY3502-4 has a USB output that can provide an additional 5V supply to auxiliary components.

### Switch and low voltage cutoff circuit

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/slide-switch.png" resize="400x" declaredimensions=true alt="The switch mounted on the Viam rover 2" />

A slide switch is connected to the rover.
Use it to turn the power on and off.

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/circuit.png" resize="400x" declaredimensions=true alt="Low-voltage cutoff circuit" />

Mounted above the switch is a low voltage cutoff circuit that can be set to turn off power to the rover when the input voltage drops below a pre-set threshold.
This can be helpful for preventing batteries fully discharging which can damage lithium ion batteries.

### Battery holders

The Viam Rover 2 comes with two battery holder options.
The rover nominally operates with four 18650 batteries, but a higher capacity RC-type battery can be mounted into the rear of the rover.

In this workshop, we'll work with four (4) 18650 batteries.

#### 18650 battery pack

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/battery-pack.png" resize="400x" declaredimensions=true alt="A battery pack" />

18650 batteries are the nominal power supply recommended for use with the Viam Rover 2.
An 18650 battery is a lithium-ion rechargeable battery.
We recommend the button-top type, though either button or flat top can work.
Any brand is suitable as long as you comply with the battery safety requirements.

#### Mount for RC-type battery

<img src="https://docs.viam.com/appendix/try-viam/rover-resources/viam-rover-2/RC-mount.png" resize="400x" declaredimensions=true alt="RC battery mount" />

You can mount a larger capacity RC-type battery into the rover.
You must wire the appropriate connector into the switch circuit.

RC-batteries are lithium-ion rechargeable batteries.
Caution should always be taken when using such batteries, always comply with the battery safety requirements.
Check the [safety](#safety) section for more information.

## ⚠️ Safety

This product is not a toy and is not suitable for children under 12.

Switch the rover off when not in use.

⚠️ Lithium-ion batteries may pose a flammable hazard. This product requires four 18650 lithium-ion batteries **OR** an RC-type battery. DO NOT connect multiple power sources simultaneously.
Refer to the battery manufacturer’s operating instructions to ensure safe operation of the Viam Rover.
Dispose of lithium-ion batteries per manufacturer instructions.


⚠️ Damage may occur to the Raspberry Pi and/or Viam Rover if wired incorrectly.
Refer to the manufacturer’s instructions for correct wiring.