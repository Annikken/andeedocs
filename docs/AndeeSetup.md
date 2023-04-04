# Getting Started

This section will guide you in setting up your new Annikken Andee shield for your Arduino projects.

If you have just gotten your Annikken Andee shield, go through each step to ensure a smooth setup or you can skip to the relevant topic if you already have completed some of it.

If you come across any issues, please check our [support](https://annikken.com/support) page for your relevant product. If the solution is not available there, feel free to [contact us](https://annikken.com/about-us#contact-us).

# Annikken Andee Shield Setup

## Installing Arduino IDE

Coding for Arduino and Annikken Andee is done using the Arduino Integrated Development Environment(IDE). Before you proceed, you should ensure that you have the Arduino IDE installed on your computer.

If the Arduino IDE is not installed, proceed to download the Arduino IDE at https://www.arduino.cc/en/Main/Software. Be sure to get the latest version.


## Installing Annikken Andee Library

The Annikken Andee Library can be easily installed by using Arduino IDE's built-in library manager. Follow these steps to install the Andee Library.

1. In your Arduino IDE, select Sketch >> Include Library >> Manage Libraries.<br>
    ![](/img/install-andee-step-1.png)

2. Filter the library search by typing "andee" into the search box in the top right corner.<br>
    ![](/img/install-andee-step-2.png)
    
3. Select the latest version from the drop down menu and hit install.<br>
    ![](/img/install-andee-step-3.png)


## Installing Annikken Andee Firmware

Annikken regularly releases new firmware updates for the Andee U, iOS and Android. It is recommended that you update the firmware on your shield when a new update is released. To do so, you require the following items:

* 1x Micro SD Card.
* 1x Micro SD Card Reader/Writer (or a computer capable of reading/writing Micro SD Cards).
* 1x Arduino Board.
* 1x Annikken Andee U/iOS/Android shield.

#### Andee U/Android

This section provides instructions for firmware installation/upgrade for Annikken Andee U and Andee Android shields. Please follow the steps:

1. Download the latest firmware for your Andee shield listed below.
    * [Andee U](https://www.annikken.com/support/andee-u)
    * [Andee Android](https://www.annikken.com/support/andee-android)

2. Extract the zip file and copy "image.hex" into your Micro SD card.

3. Connect the Annikken Andee to the Arduino and power it up. You should see an LED blinking. The Andee is in "Normal Mode".

4. We will now need to put the Andee into "Update Mode". Press and hold down the "BOOT" and "ANDEE RESET" buttons together. Don’t let go of them yet!

5. While still holding down the "BOOT" button, release the "ANDEE RESET" button.

6. Now let go of the "BOOT" button. You should see that "CONN" and "STATUS" LEDS are now flashing together.

7. Insert the Micro SD card containing "image.hex" you loaded earlier into the Annikken Andee's SD card slot. Annikken Andee will automatically start updating. The LEDs will flash red and green consecutively. Do not power down the shield at this time.

8. Once the update/installation has completed, the "CONN" and "STATUS" LEDs will start to blink green again.


You're done! Your Annikken Andee Shield is now updated with the latest firmware!


#### Andee iOS

This section provides instructions for firmware installation/upgrade for Annikken Andee iOS shields. Please follow the steps:

1. Download the latest firmware for Andee iOS [here](https://www.annikken.com/support/andee-ios).

2. Extract the zip file and copy "image.hex" into your Micro SD card.

3. Connect the Annikken Andee to the Arduino and power it up. You should see an LED blinking. The Andee is in "Normal Mode".

4. We will now need to put the Andee into "Update Mode". Press and hold down the "BTN_0" and "BTN_1" buttons together. Don’t let go of them yet!

5. While still holding down the "BTN_1" button, release the "BTN_0" button.

6. Now let go of the "BTN_1" button. You should see that "CONN" and "STATUS" LEDS are now flashing together.

7. Insert Micro SD card containing "image.hex" you loaded earlier into the Annikken Andee's SD card slot. Annikken Andee will automatically start updating. The LEDs will flash red and green consecutively. Do not power down the shield at this time.

8. Once the update/installation has completed, the "CONN" and "STATUS" LEDs will start to blink green again.


You're done! Your Annikken Andee iOS shield is now updated with the latest firmware!

 






