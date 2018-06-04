# Fast-Fingers

#include<LiquidCrystal.h>

LiquidCrystal lcd(12,13,5,4,3,2);

int btN0 = 6;
int btN1 = 7;
int btN2 = 8;
int btN3 = 9;
int btN4 = 10;

int led = 11;


void setup(){
  lcd.begin(16,2);

  pinMode(btN0, INPUT_PULLUP);
  pinMode(btN1, INPUT_PULLUP);
  pinMode(btN2, INPUT_PULLUP);
  pinMode(btN3, INPUT_PULLUP);
  pinMode(btN4, INPUT_PULLUP);

  pinMode(led, OUTPUT);

}

void AfisareText(String text){
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print(text);
  
}
void ExitGame(){
  AfisareText("Resetare joc ...");
  digitalWrite(led, LOW);
  delay (1000);
}
void loop(){
  // Citeste valoarea butoanelor
  int val0 = digitalRead(btN0);
  int val1 = digitalRead(btN1);
  int val2 = digitalRead(btN2);
  int val3 = digitalRead(btN3);
  int val4 = digitalRead(btN4);
  
  AfisareText("Starting ...");

  delay(1000);

  bool work = true;
  while(work){
      digitalWrite(led, HIGH);

      int randomNr = random(0,5);
      if (randomNr == 1){
        AfisareText("GAME: A*C***D");
        delay(500);
        AfisareText("GAME: *******");
        while (true){
          val0 = digitalRead(btN0); val1 = digitalRead(btN1); val2 = digitalRead(btN2); val3 = digitalRead(btN3); val4 = digitalRead(btN4);
          if(val0 == 0 && val1 == 1 && val2 == 1 && val3 == 0){ AfisareText("Ai castigat!!!"); digitalWrite(led, LOW); delay(1000); work = false; break; }
          if (val4 == 0){ ExitGame(); work = false;  break; }
          delay(100);
         }
      }else if (randomNr == 2){
        AfisareText("GAME: **A*D**");
        delay(500);
        AfisareText("GAME: *******");
        while (true){
          val0 = digitalRead(btN0); val1 = digitalRead(btN1); val2 = digitalRead(btN2); val3 = digitalRead(btN3); val4 = digitalRead(btN4);
          if(val0 == 0 && val1 == 1 && val2 == 1 && val3 == 0){ AfisareText("Ai castigat!!!"); digitalWrite(led, LOW); delay(1000); work = false; break; }
          if (val4 == 0){ ExitGame(); work = false;  break; }
          delay(100);
         }
      }else if (randomNr  == 3){
        AfisareText("GAME: C*****A");
        delay(500);
        AfisareText("GAME: *******");
        while (true){
          val0 = digitalRead(btN0); val1 = digitalRead(btN1); val2 = digitalRead(btN2); val3 = digitalRead(btN3); val4 = digitalRead(btN4);
          if(val0 == 0 && val1 == 1 && val2 == 0 && val3 == 1){ AfisareText("Ai castigat!!!"); digitalWrite(led, LOW); delay(1000); work = false; break; }
          if (val4 == 0){ ExitGame(); work = false;  break; }
          delay(100);
         }
      }else if (randomNr == 4){
        AfisareText("GAME: B*A*D**");
        delay(500);
        AfisareText("GAME: *******");
        while (true){
          val0 = digitalRead(btN0); val1 = digitalRead(btN1); val2 = digitalRead(btN2); val3 = digitalRead(btN3); val4 = digitalRead(btN4);
          if(val0 == 0 && val1 == 0 && val2 == 1 && val3 == 0){ AfisareText("Ai castigat!!!"); digitalWrite(led, LOW); delay(1000); work = false; break; }
          if (val4 == 0){ ExitGame(); work = false;  break; }
          delay(100);
         }
      }else{
        AfisareText("GAME: A*B*C*D");
        delay(500);
        AfisareText("GAME: *******");
        while (true){
          val0 = digitalRead(btN0); val1 = digitalRead(btN1); val2 = digitalRead(btN2); val3 = digitalRead(btN3); val4 = digitalRead(btN4);
          if(val0 == 0 && val1 == 0 && val2 == 0 && val3 == 0){ AfisareText("Ai castigat!!!"); digitalWrite(led, LOW); delay(1000); work = false; break; }
          if (val4 == 0){ ExitGame(); work = false;  break; }
          delay(100);
         }
      }
  }
  



  

}
