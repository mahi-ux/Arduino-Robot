# Arduino-Robot
String readString;
void setup() {
  // put your setup code here, to run once:
Serial.begin(9600);
pinMode(5, OUTPUT);
pinMode(6,OUTPUT);
 pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(2,OUTPUT);
  pinMode(9,OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
while(Serial.available()){
  delay(3);
  char c = Serial.read();
  readString+=c;
}

if(readString.length() >0)
{
  Serial.println(readString);
if(readString == "left")
  {
  analogWrite(2,128);
  analogWrite(9,128);
  digitalWrite(5, HIGH);
  digitalWrite(6,LOW);
  digitalWrite(10,LOW);
  digitalWrite(11,LOW);
  
  }
 else if(readString == "right")
  {
  analogWrite(2,128);
  analogWrite(9,128);
  digitalWrite(5,LOW);
  digitalWrite(6,LOW);
  digitalWrite(10,HIGH);
  digitalWrite(11,LOW);
  }
  else if(readString =="forward")
  {
    
    digitalWrite(5,HIGH);
    digitalWrite(6,LOW);
    digitalWrite(10,HIGH);
  digitalWrite(11,LOW);
}
  else if(readString =="backward")
  {
    digitalWrite(5,LOW);
    digitalWrite(6,HIGH);
    digitalWrite(10,LOW);
  digitalWrite(11,HIGH);
  }
    else if(readString =="stop")
  {
    
    digitalWrite(5,LOW);
    digitalWrite(6,LOW);
    digitalWrite(10, LOW);
  digitalWrite(11,LOW);
  }
  readString = "";
}
}
