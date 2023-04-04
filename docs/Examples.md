# Examples

This section provides examples for your Andee shield. You can jump to the example that best suits your needs.

## Creating Widgets

To create a new widget, you will need to instantiate a new instance of the AndeeHelper class as follows. The ideal place to place this would be just below your #includes declaration in your Arduino sketch.

```cpp
AndeeHelper widget1;
```

When creating a new widget, the most important properties that you need to set are:

1. **Unique ID**
2. **Screen location**
3. **Type**
4. **Colors**
5. **Display data**
 
Lets go through each of these properties.

1. **Unique ID**
To set the id:
```cpp
widget1.setId(0);
widget2.setId(1);
```
**Note:** The integer id for each widget should be unique and different. Declaring a widget as the same id as another will cause the latest widget to override the other.

2. **Screen Location**
You can set the location of your widget by one of two methods:
  * A row and column based system.
  The mobile devices is divided into 4 rows and 4 columns.
```cpp
widget1.setLocation(1, 2, ONE_THIRD);
```
    For an in depth explanation on setLocation(), refer to this [documentation](/AnnikkenAndee/AndeeAPI.md#setlocat)
  
  * Cartesian based system.
  This system is based on x and y coordinate with its origin at the top left corner, along with its height and width. 
```cpp
widget1.setCoord(25, 25, 50, 25);
```
  For an in depth explanation on setCoord() refer to this [documentation](/AnnikkenAndee/AndeeAPI.md#setcoord)

3. **Type**
The Andee library provides a few different types of UI. To see how the widgets look like, refer to [Andee U/iOS](https://annikken.com/andee-u) or [Andee Android](https://annikken.com/andee-android).
```cpp
widget1.setType(DATA_OUT);
```
For an in depth explanation on setType() and options for type, refer to this [documentation](/AnnikkenAndee/AndeeAPI.md#settype)

4. **Colors**
Every component of the widget can be customised by color.
To set the color of the titles.
```cpp
widget1.setTitleTextColor("FFAEDE94");
```
To set the background color for title region.
```cpp
widget1.setTitleColor("FFFFDAAA");
```
To set body text color.
```cpp
widget1.setTextColor("FFFFDAAA");
```
To set body background color.
```cpp
widget1.setColor("FF6D92A0");
```
For an in depth explanation to set colours and predefined colors, refer to this [documentation](/AnnikkenAndee/AndeeAPI.md#setcolor)

5. **Display Data**
To display text or data. We use the following methods.
```cpp
widget1.setTitle("Sensor A103");
widget1.setData("No readings received.");
widget1.setUnits("cm");
```


Now lets combine what we have shown into a single code snippet.
```cpp
void setup() {
    Andee.begin();
    
    widget1.setId(0);
    widget1.setCoord(25, 25, 50, 25);
    widget1.setType(DATA_OUT);
    widget1.setTitleTextColor("FFAEDE94");
    widget1.setTitleColor("FFFFDAAA");
    widget1.setTextColor("FF9A73A9");
    widget1.setColor("FF6D92A0");
    widget1.setTitle("Sensor A103");
    widget1.setData("No readings received.");
    widget1.setUnits("cm");
}
```

Certain types of widgets require extra methods for setup. They will be discussed below.

### Creating Buttons
Buttons have 2 modes. A single press mode which waits for a response from the Andee shield and a multipress mode that can be press continuously.

The button defaults to single press when instantiated. To set the button as multi press mode. Use the following code.
```cpp
button.setInputMode(ACK);
```

### Creating Input Buttons
Input buttons consists of the following:

* Keyboard Input Button
* Time Input Button
* Date Input Button

**Keyboard Input Button**

Keyboard input can activate different keyboard modes: `KEYBOARD_IN`, `ALPHA_NUMERIC`, `ALPHA_NUMERIC_PW`, `NUMERIC`, `NUMERIC_PW`.
You can set the modes with the code below.
```cpp
keyboardWidget.setInputMode(KEYBOARD_IN);
```

**Time Input Button**

You can set a initial time to display for this widget.
```cpp
timeWidget.setDefaultTime(05,30,00);
```

**Date Input Button**

You can set a initial date to display for this widget.
```cpp
dateWidget.setDefaultDate(25, DEC, 2013);
```

### Creating Analog Dials
Setting the colors for Analog Dials uses a different set methods compared to other widgets. To set the colours, use the code below.
```cpp
analogDial.setBaseColor(LIME_GREEN);
analogDial.setActiveColor(GREEN);
```
You also have to set the minimum and maximum value of the dial.
```cpp
analogDial.setMinMax(0, 100);
```

### Creating Sliders
Sliders require a number of methods to get going.
To set the slider's minimum and maximum values.
```cpp
slider.setSliderMinMax(0, 255, 0);
```
To set the initial value.
```cpp
slider.moveSliderToValue(100);
```
To set the incremental intervals for each increase in value.
```cpp
slider.setSliderNumIntervals(256);
```
The slider have 2 modes in which it can operate: `ON_VALUE_CHANGE` AND `ON_FINGER_UP`.
`ON_VALUE_CHANGE` means that the shield is updated immediately with new data when the slider is moved.
`ON_FINGER_UP` means that the shield will only be updated when the finger is lifted up from the screen after dragging the slider.
To set the mode.
```cpp
slider.setSliderReportMode(ON_VALUE_CHANGE);
```
Setting the colors for sliders uses a different set methods compared to other widgets. To set the colours, use the code below.
```cpp
slider.setActiveColor(BLUE);
slider.setBaseColor(DARK_BLUE);
```

## Updating The Widget
Sending data to your mobile device requires setting new content for your widget and updating it.
By setting new content, you can change text colors, background colors and text. 

For example, first you can change body color and data text.
```cpp
widget1.setData("New incoming data");
widget1.setColor("FF6D92A0");
```

Next, to update the widget.
```cpp
widget1.update();
```
**Note**: ```update()``` is a resource intensive process. It is recommend to only update a widget if it is needed

## Receiving Data
Widgets such as button, slider, button inputs take inputs from your mobile devices. To process this inputs on your Arduino, we need to receive that data.

**Button**
You can check if button has been pressed by using ```isPressed()```.
```cpp
if (button.isPressed()) {
    // turn on lights
}
```
You also can check the number of times the button has been pressed in a short duration
```cpp
if (button.isPressed() >= 2) {
    // turn on hall lights
} else {
    // turn on kitchen lights
}
```

**Slider**
To get the slider value
```cpp
int sliderIntValue = 0;
sliderInt.getSliderValue(&sliderIntValue,INT);

float sliderFltValue = 0; 
sliderFloat.getSliderValue(&sliderFltValue ,FLOAT);
```

**Keyboard Input Button**
First, we need to declare an array of characters to store data in memory.
```cpp
char userInput[32];
```
Next, we have to clear the memory from any data previously stored inside.
```cpp
memset(userInput, 0x00, 32);
```
Finally, we will get the data and store it inside userInput.
```cpp
textInputButton.getKeyboardMessage(userInput);
```

**Time Input Button**
First, we need to declare an array of characters to store data in memory and variables to store integers.
```cpp
int hh, mm, ss;
char tempStringTime[20];
```
Next, we will extract the hour, minute and seconds data into the ```int``` variables.
```cpp
timeInputButton.getTimeInput(&hh, &mm, &ss);
```
Lastly, we can combine the data into a string as declared before.
```cpp
sprintf(tempString, "%02d:%02d:%02d", hh, mm, ss);
```

**Date Input Button**
First, we need to declare an array of characters to store data in memory and variables to store integers.
```cpp
int dd, mm, yyyy;
char tempStringDate[20];
```
Next, we will extract the hour, minute and seconds data into the ```int``` variables.
```cpp
timeInputButton.getTimeInput(&dd, &mm, &yyyy);
```
Lastly, we can combine the data into a string as declared before.
```cpp
sprintf(tempString, "%02d/%02d/%02d", dd, mm, yyyy);
```

<br>











