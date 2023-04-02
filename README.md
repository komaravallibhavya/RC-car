# RC-car
Remote controlled car using tinkercad
const int trigPin=13;
const int echoPin=12;
char c;//status
void setup()
{ 
  Serial.begin(9600);
  pinMode(10,OUTPUT); //buzzer output pin
//for headlights
  pinMode(9, OUTPUT);
  pinMode(8, OUTPUT);
  
  //for backlights
  pinMode(13, OUTPUT);
  pinMode(12, OUTPUT);
  
  //for motor(wheels)
  pinMode(7,OUTPUT);//input 4
  pinMode(6,OUTPUT);//input 3
  pinMode(5,OUTPUT);//input 2
  pinMode(4,OUTPUT);//input 1 
  
  pinMode(2,OUTPUT); 
  pinMode(3,OUTPUT); //enable 3&4
  pinMode(11,OUTPUT);// enable 1&2
  delay(500);
  analogWrite(11, 255);
  analogWrite(3, 255);
 int distance;
  int duration;
}
void loop() 
{
  if(Serial.available())
  { c=Serial.read();
   Serial.println(c);
  }
    if(c=='H')
    {
Serial.println("headlights Blinking");
        		        digitalWrite(9,HIGH);
                        digitalWrite(8,HIGH);
                        delay(1000);
                        digitalWrite(9,LOW);
                        digitalWrite(8,LOW);
      delay(10);
                         
    }
    if(c=='J')
    {
        	Serial.println("backlights blinking");
        		        digitalWrite(13,HIGH);
                        digitalWrite(12,HIGH);
      delay(10);
       digitalWrite(13,LOW);
                        digitalWrite(12,LOW);
        delay(10);
    }            
             
      if(c=='F')
      {
       Serial.println("Forward");   
                        digitalWrite(7,LOW);
                        digitalWrite(6,HIGH);
                        digitalWrite(5,LOW);
                        digitalWrite(4,HIGH);
        				digitalWrite(2,LOW);
          delay(10);
      }
    if(c=='L')
    {
       Serial.println("Left"); 
                        digitalWrite(7,HIGH);
                        digitalWrite(6,LOW);
                        digitalWrite(5,LOW);
                        digitalWrite(4,HIGH);
        				digitalWrite(2,LOW);
        delay(10);
    }
    if(c=='S')
    {
   Serial.println("Stop"); 
                         digitalWrite(7,HIGH);
                         digitalWrite(6,HIGH);
                         digitalWrite(5,HIGH);
                         digitalWrite(4,HIGH);
        	             digitalWrite(2,HIGH);
        delay(10);
    }
    if(c=='R')
    {
        Serial.println("Right"); 
                         digitalWrite(7,LOW);
                         digitalWrite(6,HIGH);
                         digitalWrite(5,HIGH);
                         digitalWrite(4,LOW);
        		 digitalWrite(2,LOW);
        delay(10);
    }
    if(c=='B')
    {
       Serial.println("Back");  
                         digitalWrite(7,HIGH);
                         digitalWrite(6,LOW);
                         digitalWrite(5,HIGH);
                         digitalWrite(4,LOW);
        	            digitalWrite(2,LOW);
      delay(10);
    }
    if(c=='E')
    { Serial.println("Buzzer");
    tone(10, 220, 100);
    delay(200);
    }
    if(c=='A'){
      Serial.println("accelerate");
  // Accelerate from zero to maximum speed
for (int i = 0; i < 256; i++) {
analogWrite(11, i);
analogWrite(3, i);
delay(10);
}
       pinMode(7,LOW);
  pinMode(6,LOW);
  pinMode(5,LOW);
  pinMode(4,LOW);
    }
    if(c=='D'){
      Serial.println("deaccelerate");
// Decelerate from maximum speed to zero
for (int i = 255; i >= 0; --i) {
analogWrite(11, i);
analogWrite(3, i);
delay(100);
}
if(c=='dist'){
        Serial.println("find distance");
        digitalWrite(trigPin,LOW);
  delayMicroseconds(2);
  
  digitalWrite(trigPin,HIGH);
  delayMicroseconds(10);
       
    }
    }
}
