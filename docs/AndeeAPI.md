# Annikken Andee Library
These are all the functions that can be found in the Andee Library

## Andee functions
The `Andee` Class has general functions that affects the way the Andee Shield works or what it does.


### Begin
```cpp
class void begin()
```
This function is required to be called before calling any other `Andee` functions. This will setup the SPI communication on the Arduino Shield. The Slave Select pin will default to pin 8.
```cpp
class void begin(pin)
```
If the `Andee` Slave Select pin conflicts with another shield, you can use argument `pin` to change the `Andee` Slave Select pin.
##### Example
```cpp
Andee.begin();
Andee.begin(5);
```



### Change Andee Name
```cpp
class void setName(name)
```
This function will change the name of the Andee Shield. This name will appear when scanning for your Andee Shield in the app. Only works on Firmware 2.00 and above.
`name` is a `Character Array`
##### Example
```cpp
Andee.setName("My New Name");
```



### Clear All Widgets
```cpp
class void clear()
```
This function will clear all the widgets on the screen in the iOS/Android app
##### Example
```cpp
Andee.clear();
```



### Disconnect
```cpp
class void disconnect()
```
This function will force the Andee Shield to disconnect from the iOS/Android device that it is connected to
##### Example
```cpp
Andee.disconnect();
```



### Check Connection
```cpp
class int isConnected()
```
This function checks if the Andee Shield is connected to a device and returns an Integer.
If the value returned is :<br/>
`0`, the Andee Shield is not connected to a device<br/>
`1`, the Andee Shield is connected to a device
##### Example
```cpp
connected = Andee.isConnected();
```



### Get Device Time
```cpp
class void getDeviceTime(*hour,*min,*sec)
```
This function will get the time from the device that it is connected to.
The time from the device will be stored in the `hour`,`min` and `sec` arguments in `Integer`
##### Example
```cpp
Andee.getDeviceTime(&hour,&min,&sec);
```



### Get Device Date
```cpp
class void getDeviceDate(*day,*month,*year)
```
This function will get the date from the device that it is connected to.
The date from the device will be stored in the `day`, `month` and `year` arguments in `Integer`
##### Example
```cpp
Andee.getDeviceDate(&day,&month,&year)
```



### Get Timestamp
```cpp
class long getDeviceTimeStamp()
```
This function will get and return the timestamp in millis from the device that it is connected to.
The return value will be a `Long`
##### Example
```cpp
timeStamp = Andee.getDeviceTimeStamp();
```


## Using Device Features
The functions below makes use of the functions on the smart device. If the device does not have a particular feature, for example not all smartphones have a gyroscope, then the function will not work


### Vibrate Device
```cpp
class void vibrate()
```
This function will cause the connected device to vibrate for approximately 1 second
##### Example
```cpp
Andee.vibrate();
```



### Gyroscope Sensor
```cpp
class void gyroInit(interval,iteration)
```
This function will activate the gyroscope sensor on the device. The function can only be called once, unless the arguments are changed. The iOS/Android device will restart the interval timer each time this function is called.<br/>
`interval`, is an `Integer`, will set the time interval in ms before sending another gyro data.<br/>
`iteration`, is an `Integer`, will set the amount of times the gyro data should be sent.
Set `iteration` to `-1` for infinite iterations<br/>

Once the initialisation has been called, call the function below to get the gyroscope values.
```cpp
class void getGyroReading(*xAxis,*yAxis,*zAxis)
```
The values from the gyroscope sensor will be stored in the `xAxis`,`yAxis` and `zAxis` arguments in `Float`<br/>

The readings can be stopped anytime by calling
```cpp
class void gyroStop()
```
##### Example
```cpp
Andee.gyroInit(200,-1);//App will send data unlimited times at 200ms interval

Andee.getGyroReading(&xAxis,&yAxis,&zAxis);

Andee.gyroStop();
```



### Linear Accelerometer Sensor
```cpp
class void lacInit(interval,iteration)
```
This function will activate the Linear Accelerometer(LAC) sensor on the device. The function can only be called once, unless the arguments are changed. The iOS/Android device will restart the interval timer each time this function is called.<br/>

`interval`, is an `Integer`, and will set the time interval in ms before sending another LAC data.<br/>
`iteration`, is an `Integer`, and will set the amount of times the LAC data should be sent.
Set `iteration` to `-1` for infinite iterations<br/>

Once the initialisation has been called, call the function below to get the LAC values.
```cpp
class void getLacReading(*xAxis,*yAxis,*zAxis)
```
The values from the LAC sensor will be stored in the `xAxis`,`yAxis` and `zAxis` arguments in `Float`<br/>

The readings can be stopped anytime by calling
```cpp
class void lacStop()
```
##### Example
```cpp
Andee.lacInit(200,-1);//App will send data unlimited times at 200ms interval

Andee.getLacReading(&xAxis,&yAxis,&zAxis);

Andee.lacStop();
```



### Gravity Sensor
```cpp
class void gravInit(interval,iteration)
```
This function will activate the gravity sensor on the device. The function can only be called once, unless the arguments are changed. The iOS/Android device will restart the interval timer each time this function is called.<br/>

`interval`, is an `Integer`, will set the time interval in ms before sending another gravity data.<br/>
`iteration`, is an `Integer`, will set the amount of times the gravity data should be sent.
Set `iteration` to `-1` for infinite iterations<br/>

Once the initialisation has been called, call the function below to get the gravity values.
```cpp
class void getGravReading(*xAxis,*yAxis,*zAxis)
```
The values from the gravity sensor will be stored in the `xAxis`,`yAxis` and `zAxis` arguments in `Float`<br/>

The readings can be stopped anytime by calling
```cpp
class void gravStop()
```
##### Example
```cpp
Andee.gravInit(200,-1);//App will send data unlimited times at 200ms interval

Andee.getGravReading(&xAxis,&yAxis,&zAxis);

Andee.gravStop();
```



### GPS Sensor
```cpp
class void gpsInit(interval,iteration)
```
This function will activate the GPS sensor on the device. The function can only be called once, unless the arguments are changed. The iOS/Android device will restart the interval timer each time this function is called.<br/>

`interval`, is an `Integer`, will set the time interval in ms before sending another GPS data.<br/>
`iteration`, is an `Integer`, will set the amount of times the GPS data should be sent.
Set `iteration` to `-1` for infinite iterations<br/>

Once the initialisation has been called, call the function below to get the GPS values.
```cpp
class void getGpsReading(*xAxis,*yAxis)
```
The values from the GPS sensor will be stored in the `xAxis` and `yAxis` arguments in `Float`<br/>
The readings can be stopped anytime by calling
```cpp
class void gpsStop()
```
##### Example
```cpp
Andee.gpsInit(200,-1);//App will send data unlimited times at 200ms interval

Andee.getGpsReading(&xAxis,&yAxis);

Andee.gpsStop();
```


### Taking Photos
```cpp
class void takePhoto(cameraType,autoFocus,flash)
```
This function will make the connected device take 1 photo depending on the arguments below<br/>
For `cameraType` use either
* `CAM_DEFAULT` to use default camera
* `FRONT` to use Front Camera
* `BACK` to use Rear Camera <br/>
For`autoFocus` use
* `ON` to switch on auto focus
* `OFF` to switch off auto focus <br/>
For `flash` use
* `ON` to switch on flash
* `OFF` to switch off flash
##### Example
```cpp
Andee.takePhoto(BACK,ON,ON);
```



### Text to Speech
```cpp
class void textToSpeech(speech,speed,pitch,accent)
```
This function will activate the text to speech(TTS) function on the device. The app will then speak the text in the speech string. The arguments are<br/>
`speech`, is a `Character Array`, that the device will speak<br/>
`speed`, is a `Float`, is the speed of the speech<br/>
`pitch`, is a `Float`, is the pitch of the voice<br/>
`accent` of the voice. Use <br/>
* `US`
* `GREAT_BRITON`
* `AUSTRALIA`
* `IRELAND`
* `SOUTH_AFRICA`<br/>
Android devices require installation of the required language pack to use different accents.
##### Example
```cpp
Andee.textToSpeech("This is Annikken Andee",1.0,0.5,US);
```



### Notification
```cpp
class void notification(title,message,ticker)
```
This function will pop a notification on the connected device. This only works on **Android devices**. The arguments are<br/>
`title`, is a `Character Array`, is the title of the notification<br/>
`message`, is a `Character Array`, is the main text of the notification<br/>
`ticker`, is a `Character Array`, is the small text when the notification has not been expanded yet
##### Example
```cpp
Andee.notification("Andee Notify","Just some text for the body of the SMS","Andee");
```


-----------------------


## AndeeHelper Functions
The `AndeeHelper` Class has functions that help the user create the widgets on the app. A new instantiation of the class has to be made for each widget. For example,
```cpp
AndeeHelper widget1;//1 instantiation
AndeeHelper widget2;//Another instantiation

widget1.setId(5);//when using one of the functions below
```
You can then use the functions below with each instantiation. Every example from here onwards will use widget1 as the example.



### Set Id
```cpp
class void setId(id)
```
Set widget id
`id`, is a `char`, can be a number from 0 to 49
##### Example
```cpp
widget1.setId(49);
```



### Set Type
```cpp
class void setType(type)
```
`type` uses macros as the input. Available types are<br/>

* DATA_OUT
* DATA_OUT_CIRCLE
* DATA_OUT_HEADER
* BUTTON_IN
* CIRCLE_BUTTON
* ANALOG_DIAL_OUT
* KEYBOARD_IN
* DATE_IN
* TIME_IN
* SLIDER_IN
* TEXTBOX
* TTS
* JOYSTICK

##### Example
```cpp
widget1.setType(DATA_OUT);
```



### Set Location
```cpp
class void setLocation(row,column,span)
```
`row`, is a `char`, can be a number from 0 to 3<br/>
`column`, is a `char`, can be a number from 0 to 3<br/>
`span` uses macros as the input. Available macros are<br/>

* ONE_THIRD
* TWO_THIRD
* ONE_QUART
* THREE_QUART
* HALF
* FULL

##### Example
```cpp
widget1.setLocation(2,2,ONE_THIRD);
```



### Set Coordinates
```cpp
class void setCoord(xCoordinate,yCoordinate,width,height)
```
`xCoordinate`, is an `Integer`, can be a number from 0 to 100<br/>
`yCoordinate`, is an `Integer`, can be a number from 0 to 100<br/>
`width`, is an `Integer`, can be a number from 0 to 100<br/>
`height`, is an `Integer`, can be a number from 0 to 100
##### Example
```cpp
widget1.setCoord(0,0,100,25);
```



### Set Color
The widget has a few colors that can be customised. The widget body, widget body text, widget title and widget title text.
```cpp
class void setColor(color)
```
This is to set widget body color<br/>
```cpp
class void setTextColor(color)
```
This is to set widget body text color<br/>
```cpp
class void setTitleColor(color)
```
This is to set widget title color<br/>
```cpp
class void setTitleTextColor(color)
```
This is to set widget title text color<br/>

`color` is a `Character Array`. `color` should be a color hex in the form of AARRGGBB, where A is alpha, R is red, g is green and B is blue. For example, "FFFF0000" is red. There are also macros that can be used. All the possible macros will be listed [here](Andee_Color.md).<br/>
##### Example
```cpp
widget1.setColor(WHITE);
widget1.setTextColor(RED);
widget1.setTitleColor(DARK_RED);
widget1.setTitleTextColor(WHITE);
```



### Set Data
```cpp
class void setData(data)
class void setData(dataFloat,decimalPlace)
```
This function sets the widget data display.<br/>
`data` can accept an `Integer`and a `Character Array`<br/>
`dataFloat` accepts a `Float` and a decimal place needs to be specified at `decimalPlace`
##### Example
```cpp
widget1.setData(345);
or
widget1.setData("Info Here");
or
widget1.setData(1.345,3);
```



### Set Title
```cpp
class void setTitle(title)
class void setTitle(titleFloat,decimalPlace)
```
This function sets the widget title display.<br/>
`title` can accept an `Integer`and a `Character Array`. <br/>
`titleFloat` accepts a `Float` and a decimal place needs to be specified at `decimalPlace`
##### Example
```cpp
widget1.setTitle(345);
or
widget1.setTitle("Header Here");
or
widget1.setTitle(1.345,3);
```



### Set Units
```cpp
class void setUnit(units)
class void setUnit(unitFloat,decimalPlace)
```
This function sets the widget units display.<br/>
`units` can accept an `Integer`and a `Character Array`. <br/>
`unitFloat` accepts a `Float` and a decimal place needs to be specified at `decimalPlace`
##### Example
```cpp
widget1.setUnit(345);
or
widget1.setUnit("Extra Info Here");
or
widget1.setUnit(1.345,3);
```



### Update Widget
```cpp
class void update()
```
This function is very important to the Annikken Andee. If this function is not called, the widget will not appear. This function can be called at specific parts of the sketch to control the way the widget is updated.
##### Example
```cpp
widget1.update();
```



### Remove Widget
```cpp
class void remove()
```
This function tells the connected device to remove the corresponding widget when called.
##### Example
```cpp
widget1.remove();
```



### Set Min Max
**Note:**This function is only for `Slider` and `Analog Circle` Widgets
```cpp
class void setMinMax(min,max)
class void setMinMax(minFloat,maxFloat,decimalPlace)
```
This function sets the minimum and maximum value for the `Slider` and `Analog Circle` widgets.<br/>
`min` and `max` are `Integer`. <br/>
`minFloat` and `maxFloat` are `Float` and a decimal place needs to be specified at `decimalPlace`
##### Example
```cpp
widget.setMinMax(0,50)
or
widget1.setMinMax(0.00,50.00,2);
```


## Input Widget Functions
** The functions below are only needed if the `Slider`,`Button`,`Circle Button`,`Date`,`Time` and `Keyboard` widgets are used**


### Set Input Mode
```cpp
class void setInputMode(mode)
```
`mode` uses macros as the input. Available macros are: <br/>
For `BUTTON_IN` and `CIRCLE_BUTTON`, use `ACK` for acknowledged button presses or `NO_ACK` for a multi press button.<br/>

For `SLIDER_IN`, use `ON_FINGER_UP` for a slider that updates the value upon lifting the finger from the screen,`ON_VALUE_CHANGE` for a slider that updates the value as soon as the values change or `NO_FINGER` for a slider that looks like a progress bar,with no interaction needed<br/>

For `KEYBOARD_IN`, use `ALPHA_NUMERIC` for AlphaNumeric Keyboard, `ALPHA_NUMERIC_PW` for AlphaNumeric keyboard that hides the typed character after a few seconds, `NUMERIC` for a Numeric Keyboard with symbols or `NUMERIC_PW` for a Numeric Keyboard that hides typed characters after a few seconds<br/>

Both `Date` and `Time` only have 1 input mode
##### Example
```cpp
widget1.setType(BUTTON_IN);
widget1.setInputMode(ACK);
```


## Slider Widget Specific Functions
**The next 3 functions are only used for slider widgets**


### Move Slider Thumb
```cpp
class void moveSliderToValue(value)
class void moveSliderToValue(valueFloat,decimalPlace)
```
This function moves the slider thumb to the position as defined in the argument `value` or `valueFloat`<br/>
`value` is an integer. <br/>
`valueFloat` is a `Float` and a decimal place needs to be specified at `decimalPlace`
##### Example
```cpp
widget1.moveSliderToValue(50);
or
widget1.moveSliderToValue(34.4,1);
```



### Set the Number of Intervals for Slider
```cpp
class void setSliderNumIntervals(value)
```
This function sets the number of intervals (or number of steps) the slider widget has.
`value` is an `Integer`
##### Example
```cpp
widget1.setSliderNumIntervals(100);
```



### Get Slider Value
```cpp
class int getSliderValue()
class float getSliderValue()
```
This function is to get the value of the slider from the app. The function will return an `Integer` or a `Float`
##### Example
```cpp
sliderValue = widget1.getSliderValue();
```


## Button Widget Specific Functions
**The widgets `Button`,`Circle Button`,`Date` and `Time` widgets use the functions below**


### isPressed
```cpp
class int isPressed()
```
This function is used to check if a button widget has been pressed. This function returns the number of times the button has been pressed and a `0` if the button is not pressed
##### Example
```cpp
if(widget1.isPressed() > 0)
{
...........................
}
or
int buttonPressed = widget1.isPressed();
```



### Acknowledgement
```cpp
class void ack()
```
This function will send an acknowledgement packet to the connected device. This is required when the input mode of the button widget has been set to acknowledgement
##### Example
```cpp
widget1.ack();
```


## Keyboard Widget Specific Functions


### Get Keyboard Message
```cpp
class void getKeyboardMessage(*appReply)
```
This function is to get the reply when the Keyboard Widget is used. The function will store the reply in the `appReply` as a `Character Array`
##### Example
```cpp
widget1.getKeyboardMessage(&getReply);
```


## Date Widget Specific Functions


### Set Default Date
```cpp
class void setDefaultDate(day, month, year)
```
This function sets the default day when the date widget is used. When the user taps on the widget, a calendar is presented and the cursor will highlight the default day.<br/>
Both `day` and `year` are `Integer` while `month` can accept `Integer` and months in macro. The available macros are <br/>

* `Jan`
* `Feb`
* `Mar`
* `Apr`
* `May`
* `Jun`
* `Jul`
* `Aug`
* `Sep`
* `Oct`
* `Nov`
* `Dec`

##### Example
```cpp
widget1.setDefaultDate(07,Feb,2016);
```



### Get Date
```cpp
class void getDateInput(*day,*month,*year)
```
This function is used to get the date input from the Date widget. The values will be stored accordingly into `day`,`month` and `year`
##### Example
```cpp
widget1.getDateInput(&day,&month,&year);
```


## Time Widget Specific Functions


### Set Default Time
```cpp
class void setDefaultTime(hour,minute,second)
```
This function sets the default time when the Time widget is used. When the user taps on the widget, a pop up on the app will show the default time.
##### Example
```cpp
widget1.setDefaultTime(05,30,00);
```



### Get Time
```cpp
class void getTimeInput(hour,minute,second)
```
This function is used to get the time input from the Time widget. The values will be stored accordingly into `hour`,`minute`,`second`
```cpp
widget1.getTimeInput(&hour,&minute,&second);
```




