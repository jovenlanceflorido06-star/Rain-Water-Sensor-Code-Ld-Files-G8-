
const int waterSensorPin = A0;
const int buzzerPin = 9;

const int greenLED = 2;
const int redLED = 3;

int waterLevel;

// Adjust after checking your sensor readings
const int threshold = 500;

void setup() {
  pinMode(buzzerPin, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(redLED, OUTPUT);

  Serial.begin(9600);
}

void loop() {
  waterLevel = analogRead(waterSensorPin);

  Serial.print("Water Level: ");
  Serial.println(waterLevel);

  if (waterLevel > threshold) {
    // LOW / NO WATER
    digitalWrite(greenLED, HIGH);
    digitalWrite(redLED, LOW);
    digitalWrite(buzzerPin, LOW);

    Serial.println("Rain Level: LOW");
  }
  else {
    // HIGH WATER
    digitalWrite(greenLED, LOW);
    digitalWrite(redLED, HIGH);
    digitalWrite(buzzerPin, HIGH);

    Serial.println("Rain Level: HIGH");
  }

  delay(1000);
}
