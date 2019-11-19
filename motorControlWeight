#include "HX711.h"

#define DOUT  3
#define CLK  2
#define MOTOR2 5
HX711 scale(DOUT, CLK);

//int motorPin = 5;

float calibration_factor = -7050; //-7050 worked for my 440lb max scale setup

void setup() {
  Serial.begin(9600);
  Serial.println("HX711 calibration sketch");
  Serial.println("Remove all weight from scale");
  Serial.println("After readings begin, place known weight on scale");
  Serial.println("Press + or a to increase calibration factor");
  Serial.println("Press - or z to decrease calibration factor");

  scale.set_scale();
  scale.tare();	//Reset the scale to 0

  long zero_factor = scale.read_average(); //Get a baseline reading
  Serial.print("Zero factor: "); //This can be used to remove the need to tare the scale. Useful in permanent scale projects.
  Serial.println(zero_factor);

  pinMode(motorPin,OUTPUT);
    //pinMode(MOTOR2, OUTPUT);
    //Turn the Serial Protocol ON
    //Serial.begin(9600);
    while(! Serial);
   Serial.println ("Enter Desiriable time : ");
}

void loop() {
   
  scale.set_scale(calibration_factor); //Adjust to this calibration factor

  Serial.print("Reading: ");
  Serial.print(scale.get_units(), 1);
  Serial.print(" lbs"); //Change this to kg and re-adjust the calibration factor if you follow SI units like a sane person
  Serial.print(" calibration_factor: ");
  Serial.print(calibration_factor);
  Serial.println();

  if(Serial.available())
  {
    char temp = Serial.read();
    if(temp == '+' || temp == 'a')
      calibration_factor += 10;
    else if(temp == '-' || temp == 'z')
      calibration_factor -= 10;
  }

   /*  check if data has been sent from the computer: */
  //if (Serial.available())  {
    int time  = Serial.parseInt();
   // if (time >= 0 && time <= 100000)
    /* read the most recent byte */
   //time = Serial.read();
  while(1){
  //Set motor speed
    analogWrite (motorPin,30);
    delay(time); //motor runs in above speed for 5 mints
   
    analogWrite (motorPin,0);
    delay(time); //motor runs in above speed for 5 mints.
//}
}
