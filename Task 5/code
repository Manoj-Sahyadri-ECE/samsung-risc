// Speed Limit Indicator with LEDs using VSD Squadron Mini
// Uses Hall effect sensor or magnetic reed switch for speed detection

// Configuration
#define SENSOR_PIN         13  // Input pin for speed sensor
#define GREEN_LED_PIN      12  // Green LED (under limit)
#define YELLOW_LED_PIN     14  // Yellow LED (warning)
#define RED_LED_PIN        27  // Red LED (over limit)
#define NUM_MAGNETS        1   // Number of magnets per revolution
#define WHEEL_CIRCUMFERENCE 2.0 // Wheel circumference in meters
#define SPEED_LIMIT        50  // Speed limit in km/h
#define WARNING_THRESHOLD  45  // Speed for warning (yellow LED)

// Global variables
volatile unsigned long pulse_count = 0;
unsigned long last_update = 0;
float current_speed = 0.0;

void IRAM_ATTR sensorISR() {
  pulse_count++;
}

void setup() {
  Serial.begin(115200);
  
  // Initialize LED pins
  pinMode(GREEN_LED_PIN, OUTPUT);
  pinMode(YELLOW_LED_PIN, OUTPUT);
  pinMode(RED_LED_PIN, OUTPUT);
  
  // Initialize sensor pin with interrupt
  pinMode(SENSOR_PIN, INPUT_PULLUP);
  attachInterrupt(digitalPinToInterrupt(SENSOR_PIN), sensorISR, FALLING);
  
  // Initial state: all LEDs off
  digitalWrite(GREEN_LED_PIN, LOW);
  digitalWrite(YELLOW_LED_PIN, LOW);
  digitalWrite(RED_LED_PIN, LOW);
}

void loop() {
  // Update speed every second
  if (millis() - last_update >= 1000) {
    detachInterrupt(SENSOR_PIN); // Temporarily disable interrupt
    
    // Calculate RPM
    float rpm = (pulse_count * 60.0) / NUM_MAGNETS;
    
    // Calculate speed in km/h
    current_speed = (rpm * WHEEL_CIRCUMFERENCE * 60) / 1000;
    
    // Reset counters
    pulse_count = 0;
    last_update = millis();
    
    // Re-enable interrupt
    attachInterrupt(digitalPinToInterrupt(SENSOR_PIN), sensorISR, FALLING);
    
    // Control LEDs based on speed
    if (current_speed >= SPEED_LIMIT) {
      digitalWrite(RED_LED_PIN, HIGH);
      digitalWrite(YELLOW_LED_PIN, LOW);
      digitalWrite(GREEN_LED_PIN, LOW);
    }
    else if (current_speed >= WARNING_THRESHOLD) {
      digitalWrite(YELLOW_LED_PIN, HIGH);
      digitalWrite(RED_LED_PIN, LOW);
      digitalWrite(GREEN_LED_PIN, LOW);
    }
    else {
      digitalWrite(GREEN_LED_PIN, HIGH);
      digitalWrite(YELLOW_LED_PIN, LOW);
      digitalWrite(RED_LED_PIN, LOW);
    }
    
    // Serial output for debugging
    Serial.print("Speed: ");
    Serial.print(current_speed);
    Serial.println(" km/h");
  }
}
