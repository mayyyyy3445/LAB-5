# LAB-5

This is a simple Arduino push-button circuit using a pull-down resistor.

Components and Connections:
	1.	Arduino Uno: The microcontroller board used to read the button input.
	2.	Push-button (Momentary Switch): Connected to a digital input pin.
	3.	Resistor (likely 10kΩ): Used as a pull-down resistor to keep the input LOW when the button is not pressed.
	4.	Wires:
	•	Red wire: Connects the push-button to 5V.
	•	Blue wire: Connects the other side of the button to Digital Pin 2 (to read the button state).
	•	Black wire: Connects the resistor to GND.
	•	Resistor: One end is connected to GND, and the other is connected to the button and Digital Pin 2.

How It Works:
	1.	Button Not Pressed:
	•	The pull-down resistor keeps the Arduino pin at LOW (0V).
	2.	Button Pressed:
	•	The circuit completes, and 5V is sent to Digital Pin 2.
	•	The Arduino reads this as HIGH (1).

Arduino Code Example:

const int buttonPin = 2;  // Button connected to pin 2
const int ledPin = 13;    // Built-in LED on pin 13

void setup() {
  pinMode(buttonPin, INPUT);  // Set button pin as input
  pinMode(ledPin, OUTPUT);    // Set LED pin as output
  Serial.begin(9600);         // Start serial communication
}

void loop() {
  int buttonState = digitalRead(buttonPin);  // Read button state

  if (buttonState == HIGH) {
    digitalWrite(ledPin, HIGH);  // Turn LED on if button is pressed
    Serial.println("Button Pressed!");
  } else {
    digitalWrite(ledPin, LOW);   // Turn LED off if button is not pressed
  }

  delay(100);  // Small delay to stabilize readings
}

What This Code Does:
	•	Reads the button state from pin 2.
	•	If the button is pressed, it turns ON the built-in LED on pin 13 and prints “Button Pressed!” in the Serial Monitor.
	•	Otherwise, the LED remains OFF.

Possible Enhancements:
	•	Control an external LED instead of using the built-in LED.
	•	Use an interrupt instead of digitalRead() for more responsive button presses.
