# Step 5: Add a rover fragment
[Fragments](https://docs.viam.com/manage/fleet/reuse-configuration/) are shareable configurations for one or more resources that can be used across multiple machines. Here, we'll add a fragment based on the type of board you have. This fragment will include all the components you'll need to communicate and interact with your rover.

## Add your rover fragment
1. Navigate to your machine's page.
1. In the left-hand menu of the **CONFIGURE** tab, click the **+** (Create) icon next to the machine you want to add the fragment to.
1. Select **Insert fragment**. Now, you can see the available fragments to add.
1. You'll need to add the correct fragment based on your board type:
    - If you have a **Raspberry Pi 5**: Search for and select [`ViamRover2-2024-rpi5`](https://app.viam.com/fragment/11d1059b-eaed-4ad8-9fd8-d60ad7386aa2/json) and click **Insert fragment** again to add the fragment to your machine configuration:
    - If you have a **Raspberry Pi 4**: Search for and select [`ViamRover2-2024-rpi4-a`](https://app.viam.com/fragment/7c413f24-691d-4ae6-a759-df3654cfe4c8/json) and click **Insert fragment** again to add the fragment to your machine configuration:

        <img src="https://docs.viam.com/appendix/try-viam/rover-resources/fragments/fragments_list.png" resize="400x" style="width: 500px" alt="List of available fragments" class="shadow" />

1. Click **Save** in the upper right corner of the page (or hit Ctrl/Command + S) to save your new configuration.
1. The fragment adds the following components to your machine's JSON configuration:

    - A [board component](https://docs.viam.com//operate/reference/components/board/) named `local` representing the Raspberry Pi.
    - Two [motors](https://docs.viam.com//operate/reference/components/motor/gpio/) (`right` and `left`)
        - The configured pin numbers correspond to where the motor drivers are connected to the board.
    - Two [encoders](https://docs.viam.com//operate/reference/components/encoder/single/), one for each motor
    - A wheeled [base](https://docs.viam.com//operate/reference/components/base/), an abstraction that coordinates the movement of the right and left motors
        - Width between the wheel centers: 356 mm
        - Wheel circumference: 381 mm
        - Spin slip factor: 1
    - A webcam [camera](https://docs.viam.com//operate/reference/components/camera/webcam/)
    - An [accelerometer](https://github.com/viam-modules/tdk-invensense/)
    - A [power sensor](https://github.com/viam-modules/texas-instruments/)

> 💡 For information about how to configure components yourself when you are not using the fragment, click the links on each component above.

> You can also view the configured pin numbers and other values specific to the fragment:
>   - [`ViamRover2-2024-rpi5`](https://app.viam.com/fragment?id=7c413f24-691d-4ae6-a759-df3654cfe4c8) (Raspberry Pi 5)
>   - [`ViamRover2-2024-rpi4-a`](https://app.viam.com/fragment?id=7c413f24-691d-4ae6-a759-df3654cfe4c8) (Raspberry Pi 4)


## Move your rover!
1. To control your rover, navigate to the **CONTROL** tab in the Viam app.

1. Once you're on the **CONTROL** tab, find the `viam_base` (or your base component name) in the left sidebar and click on it.

1. Within the base card, toggle on the Keyboard control option. This enables you to control the rover using keyboard keys `W, A, S,` and` D`. Note that the keyboard control uses WASD keys rather than arrow keys:
    - `W` and `S` to go forward and back
    - `A` and `D` to arc and spin
