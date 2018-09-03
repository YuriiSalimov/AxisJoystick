# Axis Joystick Library

For Arduino boards.

The Library implements a set of methods for working with an axis joystick controller.
Dual axis XY joystick module reading.

The Analog Joystick is similar to two potentiometers connected together,
one for the vertical movement (Y-axis) and other for the horizontal movement (X-axis).
The joystick also comes with a button.

The Arduino Uno or any other Arduino board that uses Atmega328 as the Microcontroller
has ADC resolution of 10 bits. Hence the values on each analog channel can vary from 0 to 1023.

The home position for the stick is at (x,y:511,511). If the stick is moved on X axis
from one end to the other, the X values will change from 0 to 1023 and similar thing
happens when moved along the Y axis. On the same lines you can read position of the
stick anywhere in upper half hemisphere from combination of these values.

## Installation

1. [Download](https://github.com/YuriiSalimov/AxisJoystick/releases) the Latest release from gitHub.
2. Unzip and modify the Folder name to "AxisJoystick" (Remove the '-version')
3. Paste the modified folder on your Library folder
(On your `libraries` folder inside Sketchbooks or Arduino software).
4. Restart the Arduino IDE.

## Circuit Diagram

![Circuit Diagram](CircuitDiagram.png)

## Methods

```cpp
	/**
		SW - a digital port number of a button.
		VRx - a analog port number of X axis.
		VRy - a analog port number of Y axis.
	*/
	AxisJoystick joystick(SW, VRx, VRy);

	/**
		Enums of a possible pressings
		of the joystick controller:
			PRESS - button is pressed;
			UP - X axis is pressed up;
			DOWN - X axis is pressed down;
			RIGTH - Y axis is pressed right;
			LEFT - Y axis is pressed left;
			NOT - otherwise.
	*/
	enum Move {
		PRESS, UP, DOWN, RIGHT, LEFT, NOT
	};

	/**
		Single reading of the joystick controller.
		If the joystick is clamped, the next
		value of pressing - NOT.
		Return value of pressing the joystick:
			Move::PRESS - button is pressed;
			Move::UP - X axis is pressed up;
			Move::DOWN - X axis is pressed down;
			Move::RIGTH - Y axis is pressed right;
			Move::LEFT - Y axis is pressed left;
			Move::NOT - otherwise.
	*/
	joystick.singleRead();

	/**
		Multiple reading of the joystick controller.
		If the joystick is clamped,
		returns a pressed button value.
		Return value of pressing the joystick:
			Move::PRESS - button is pressed;
			Move::UP - X axis is pressed up;
			Move::DOWN - X axis is pressed down;
			Move::RIGTH - Y axis is pressed right;
			Move::LEFT - Y axis is pressed left;
			Move::NOT - otherwise.
	*/
	joystick.multipleRead();

	/**
		Checks if the joystick button is pressed.
		Return true - button is pressed,
		false - button is not pressed.
	*/
	joystick.isPress();

	/**
		Checks if the joystick is pressed up (X axis).
		Return true - joystick is pressed up,
		false - joystick is not pressed.
	*/
	joystick.isUp();

	/**
		Checks if the joystick is pressed down (X axis).
		Return true - joystick is pressed down,
		false - joystick is not pressed.
	*/
	joystick.isDown();

	/**
		Checks if the joystick is pressed right (Y axis).
		Return true - joystick is pressed right,
		false - joystick is not pressed.
	*/
	joystick.isRight();

	/**
		Checks if the joystick is pressed left (Y axis).
		Return true - joystick is pressed left,
		false - joystick is not pressed.
	*/
	joystick.isLeft();

	// Returns the joystick X axis coordinate  (VRx).
	joystick.readVRx();

	// Returns the joystick Y axis coordinate  (VRy).
	joystick.readVRy();

	// Returns the joystick button signal (SW).
	joystick.readSW();
```

Created by Yurii Salimov.
