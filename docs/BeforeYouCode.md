# Andee U/iOS/Android Shield

Thank you for purchasing the Annikken Andee shield! Before you start coding your first project with Annikken Andee, here are the steps required for Annikken Andee to work.

## Before You Code
In order to use the Andee101 Library in your sketch , we require the following libraries:

1. SPI.h
2. Andee.h

To include them in the project, insert the following code snippet at the top of your Arduino sketch.

```cpp
#include <SPI.h>
#include <Andee.h>
```

You will then need to add this code in the setup

```cpp
void setup() {
    Andee.begin();  // Setup communication between Annikken Andee and Arduino
}
```
to start communication between the Andee shield and Arduino board.

The final sketch will look like the code below 

```cpp
#include <SPI.h>
#include <Andee.h>

void setup() {
    Andee.begin();  // Setup communication between Annikken Andee and Arduino
	//put other setup code here if there are any
}

void loop() {
	// put your main code here, to run repeatedly:
	
}
```

**Note:** These steps are required for each project that you use with Annikken Andee. Leaving out these steps results in compile errors.

![](/assets/getting-started/gb-andee-boards.png)