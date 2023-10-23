#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <DHT.h>

#define DHTPIN 2
#define DHTTYPE DHT11

// LCD configuration
const int lcdColumns = 16;
const int lcdRows = 2;
LiquidCrystal_I2C lcd(0x27, lcdColumns, lcdRows);

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
  lcd.init();
  lcd.backlight();
  displayWelcomeMessage();
}

void loop() {
  delay(2000);

  float h = dht.readHumidity();
  float t = dht.readTemperature();

  if (isnan(h) || isnan(t)) {
    return;
  }

  lcd.clear(); // Limpa o LCD antes de exibir os novos dados
  lcd.setCursor(0, 0);
  lcd.print("Umidade: ");
  lcd.print(h);
  lcd.print("%");

  lcd.setCursor(0, 1);
  lcd.print("Temp: ");
  lcd.print(t);
  lcd.print(" C");
  delay(4000);
  lcd.clear();
  if (t > 35.0) {
    lcd.setCursor(1, 0);
    lcd.print("Calor intenso");
    delay(2500);
  }
}

void displayWelcomeMessage() {
  lcd.clear();
  lcd.print("CIEBP");
  lcd.setCursor(0, 1);
  lcd.print("Termometro");
  delay(4000); // Delay para exibir a mensagem de boas-vindas (ajuste conforme necessário)
}
