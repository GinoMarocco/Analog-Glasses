# Analog-Glasses
#include <Servo.h>

Servo servo1;  // left Lens
Servo servo2; // right lens

int pos = 0;    // variable to store the servo position
int threshold = 850;
int currentSensorVal;
int prevSensorVal;

void setup() {
  servo1.attach(9);
  servo2.attach(5);
}

void loop() {

  currentSensorVal = analogRead (A2);

  //int sensorValue = analogRead(A2);
    Serial.println(currentSensorVal);
    delay(1);

  if (currentSensorVal < threshold && prevSensorVal > threshold)
  {

    servo1.write(90);              // tell servo to go to position in variable 'pos'
    delay(15);
    servo2.write(0);
    delay(15);// waits 15ms for the servo to reach the position
  }
  if (currentSensorVal > threshold && prevSensorVal < threshold)
  {
    servo1.write(0);              // tell servo to go to position in variable 'pos'
    delay(15);
    servo2.write(90);
    delay(15);// waits 15ms for the servo to reach the position
    
  }
  prevSensorVal = currentSensorVal;

}
