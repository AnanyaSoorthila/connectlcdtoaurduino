# connectlcdtoaurduino
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Set the correct I2C address found by the scanner (replace 0x27 if needed)
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  // Initialize the LCD with dimensions
  lcd.init();
  // Turn on the backlight
  lcd.backlight();
  // Display an initial message
  lcd.setCursor(0, 0);
  lcd.print("Smart Medicine");
  lcd.setCursor(0, 1);
  lcd.print("Reminder");
  delay(2000); // Delay to show the initial message for 2 seconds
}

void loop() {
  // Array of reminder messages
  const char* reminders[] = {
    "Morning meds",
    "Take tablet-1",
    "Afternoon dosage",
    "Take tablet-2",
    "Evening meds",
    "Review daily tasks"
  };
  
  // Number of reminders
  const int numReminders = sizeof(reminders) / sizeof(reminders[0]);
  
  // Display each reminder for 10 seconds
  for (int i = 0; i < numReminders; i++) {
    lcd.clear(); // Clear the display
    lcd.setCursor(0, 0);
    lcd.print("Reminder:");
    lcd.setCursor(0, 1);
    lcd.print(reminders[i]);
    delay(10000); // Wait for 10 seconds
  }
}
