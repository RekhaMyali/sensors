# sensors
const int ledPin =(13);
const int trigPin = (10); 
const int echoPin = (9); 
const int buzzer=(8);
long duration;
int distance,safetyDistance;
void setup()
{
pinMode (ledPin, OUTPUT); //sets the digital pin 13 as output
pinMode (trigPin, OUTPUT);
pinMode (echoPin, INPUT); 
pinMode(buzzer,OUTPUT);
Serial.begin(9600);
}
void loop()
{
  //long duration;
  //int distance,safetyDistance;
digitalWrite (trigPin, LOW);//sets trig pin off
delayMicroseconds(2);//the code in program pause for 2 ms
digitalWrite (trigPin, HIGH);
delayMicroseconds(10);
digitalWrite (trigPin, LOW);
duration=pulseIn(echoPin,HIGH);
distance=duration*0.034/2;
safetyDistance=distance;
if(safetyDistance<= 5)
{
  digitalWrite(buzzer,HIGH);
  digitalWrite(ledPin,HIGH);
}
else
{
  digitalWrite(buzzer,LOW);
  digitalWrite(ledPin,LOW);
}
Serial.print("Distance:");
Serial.println(distance);
}

