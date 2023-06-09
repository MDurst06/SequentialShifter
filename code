#include <Joystick.h>

int upPin = 8;
int downPin = 5;

int Up = 0;
int Down = 0;

void setup() {
pinMode(upPin, INPUT_PULLUP);
pinMode(downPin, INPUT_PULLUP);

Joystick.begin();
}

void loop( ){

Up = digitalRead(upPin);
Down = digitalRead(downPin);

Joystick.setButton(0,!Up);
Joystick.setButton(1,!Down);

delay(50);
}
