# social-distancing-alert
the main idea of this device is to instruct the people with a device to maintain social distancing using arduino

/*---- program for smart distancing alert----*/
float temperature;
int temperaturepin=2;
float backdistance;
int backdistancepin=3;
float frontdistance;
int frontdistancepin=4;
int ledpin=12;
int buzzerpin=13;
int ledalert;
int sountalert;

void setup() {
  pinMode(temperaturepin,INPUT);   //pin  for thermal sensor
  pinMode(backdistancepin,INPUT);   //pin for ultra sonic sensor
  pinMode(frontdistancepin,INPUT);    //pin for ultra sonic sensor
  pinMode(ledpin,OUTPUT);   // pin for led
  pinMode(buzzerpin,OUTPUT);   //pin for piezo buzzer

}

void loop() {
  temperature=analogRead(temperaturepin);
  frontdistance=analogRead(backdistancepin);
  backdistance=analogRead(frontdistancepin);

/* checking the condition whether the object is living being or not  
  then it checks the condition for distance*/
  if(temperature <=98.5 && frontdistance <= 200 && backdistance <=200) 
  {
    digitalWrite(12,HIGH); // led glows
    digitalWrite(13,HIGH); // alert sound from piezo buzzer
    
  }
  else
  {
    digitalWrite(12,LOW);  // led not glows
    digitalWrite(13,LOW);  // no sound from piezo buzzer
    
  }

}
