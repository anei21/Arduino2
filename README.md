
const int sensor = A0;
const int ledR = 7;
const int ledA = 5;
const int ledV = 6;
int valor = 0; //valor que arroja el sensor
const int umbral1 = 25;
const int umbral2 = 30;
float milivolts;
float temp;//valor del sensor ya procesado en grados centigrados

void setup() {
  pinMode(ledR, OUTPUT);
  pinMode(ledA, OUTPUT);
  pinMode(ledV, OUTPUT);
  pinMode(sensor, INPUT);
}

void loop() {
  valor = analogRead(sensor);
  milivolts = 5000 * (valor / 1023.0);
  temp = milivolts / 10;
  if (temp <= umbral1) {
    digitalWrite(ledV, HIGH);
    digitalWrite(ledA, LOW);
    digitalWrite(ledR, LOW);
    delay(300);
  }
  else {
    if (umbral1 <= temp && temp <= umbral2) {
      digitalWrite(ledA, HIGH);
      digitalWrite(ledV, LOW);
      digitalWrite(ledR, LOW);
      delay(300);
    }
    else {
      if (temp > umbral2) {
        digitalWrite(ledR, HIGH);
        digitalWrite(ledV, LOW);
        digitalWrite(ledA, LOW);
        delay(500);
      }
      else {
        digitalWrite(ledA, LOW);
        digitalWrite(ledV, LOW);
        digitalWrite(ledR, LOW);
        delay(300);
      }

    }
  }
  delay(400);


}
