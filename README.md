4-Digit-7-Segment-display-with-Arduino-Mega--Compatible-with-most-Arduinos-
===========================================================================

/*

DPIN 22= Digit 1 (Left side of segment)
DPIN 23= Digit 2 (Left middle side of segment)
DPIN 24= Digit 3 (Right middle side of segment)
DPIN 25= Digit 4 (Right side of segment)
*/
int digit[] = {22, 23, 24, 25};
const int num_digits = (sizeof(digit) / sizeof(byte));

/*
  segment is looked at from left to right; top to bottom, the first pin in this array should
  be the far left LED segment, the next one is the top of the LED segment, next is right, next is middle,
  next is bottom left, next is bottom middle, next is right, This code dosen't acknowledge the use of periods.
*/

int segment[] = {47,46,48,45,27,26,44};
const int num_segments = (sizeof(digit) / sizeof(byte));


//What message should we display?
String message_to_display = "ABCD";
int message_length = message_to_display.length();

//How long (in miliseconds) should we pause and display a new update of letters?
int pause_length = 1000;

void setup(){
  Serial.begin(9600);
  
 //Turn on digit pins that we need....
 int digitPins_i;
 for(digitPins_i = 0; digitPins_i <= num_digits; digitPins_i = digitPins_i + 1){
   pinMode(digit[digitPins_i], OUTPUT);
 }
 
 //Turn on segment pins that we need....
 int segmentPins_i;
 for(segmentPins_i = 0; segmentPins_i <= num_segments; segmentPins_i = segmentPins_i + 1){
  pinMode(segment[segmentPins_i], OUTPUT); 
 }
}

void loop(){
 //Display the letters across the screen!

 int tmp_i;
 for(tmp_i = 0; tmp_i < message_length; tmp_i = tmp_i + 1){
  //Display 4 letters at a time and marquee them
   displayLetter('t', 0);
 }
}



/* 
        ===== Functions =====
*/

void displayLetter(char letter, int digitIndex){
   turnOffAllLEDS();
   
   //Turn on the digit being asked for
   digitalWrite(digit[digitIndex], HIGH);
   
   //Turn on the segments being asked for...
     if(letter == 'a'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[2], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'b'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'c'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW); 
     }else if(letter == 'd'){
      digitalWrite(segment[2], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'e'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[3], LOW); 
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
     }else if(letter == 'f'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
     }else if(letter == 'g'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'h'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[2], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'i'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[4], LOW);
     }else if(letter == 'j'){
      digitalWrite(segment[2], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'k'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[2], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'l'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
     }else if(letter == 'o'){
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'p'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[2], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
     }else if(letter == 'q'){
       digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[2], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[6], LOW);
     }else if(letter == 'r'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[4], LOW);
     }else if(letter == 's'){
       digitalWrite(segment[0], LOW);
      digitalWrite(segment[1], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[6], LOW);
      digitalWrite(segment[5], LOW);
     }else if(letter == 't'){
      digitalWrite(segment[0], LOW);
      digitalWrite(segment[3], LOW);
      digitalWrite(segment[4], LOW);
      digitalWrite(segment[5], LOW);
     }
}

void turnOffAllLEDS(){
   //Turn off digit pins....
 int digitPins_i;
 for(digitPins_i = 0; digitPins_i <= num_digits; digitPins_i = digitPins_i + 1){
   digitalWrite(digit[digitPins_i], LOW);
 }
 
 //Turn off segment pins....
 int segmentPins_i;
 for(segmentPins_i = 0; segmentPins_i <= num_segments; segmentPins_i = segmentPins_i + 1){
  digitalWrite(segment[segmentPins_i], HIGH); 
 }
}
