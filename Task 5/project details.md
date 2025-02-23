*Project Title:* Speed Limit Indicator System with LEDs using VSD Squadron Mini  

---

### *Objective*  
Develop a speed monitoring system that uses LEDs to visually indicate when a vehicle exceeds predefined speed limits. The VSD Squadron Mini (ESP32-based) processes sensor data to calculate speed and controls LEDs to show compliance/warnings.

---

### *Key Components*  
1. *VSD Squadron Mini Microcontroller* (ESP32 core)  
2. *Speed Sensor* (Hall effect sensor or magnetic reed switch)  
3. *LEDs* (Green, Yellow, Red)  
4. Resistors (220–330Ω for LEDs)  
5. Wheel with embedded magnet(s)  

---

### *Working Principle*  
1. *Sensor Input*:  
   - A magnet attached to a rotating wheel triggers the Hall effect sensor.  
   - Each rotation generates a pulse counted by the microcontroller.  

2. *Speed Calculation*:  
   - The microcontroller calculates speed using:  
     *Speed (km/h) = (Pulses × Wheel Circumference × 60) / (Number of Magnets × 1000)*  

3. *LED Indication*:  
   - *Green LED*: Speed < Warning threshold (e.g., 45 km/h).  
   - *Yellow LED*: Speed ≥ Warning threshold but < Speed limit (e.g., 45–50 km/h).  
   - *Red LED*: Speed ≥ Speed limit (e.g., 50 km/h).  

---

### *Features*  
- Real-time speed monitoring via serial output.  
- Multi-color visual feedback for speed status.  
- Configurable thresholds (SPEED_LIMIT, WARNING_THRESHOLD).  
- Low power consumption (LED-based alerts).  
- Interrupt-driven pulse counting for accuracy.  

---

### *Hardware Setup*  
1. *Sensor*: Connect Hall effect sensor to GPIO13 (interrupt-enabled pin).  
2. *LEDs*:  
   - Green LED → GPIO12  
   - Yellow LED → GPIO14  
   - Red LED → GPIO27  
3. *Parameters*:  
   - Wheel circumference (e.g., 2 meters).  
   - 1–2 magnets per wheel revolution.  

---

### *Applications*  
- Bicycles/e-bikes for safety compliance.  
- Industrial conveyor belt speed monitoring.  
- Educational tool for IoT and embedded systems.  
- Retrofit for older vehicles lacking speed alerts.  

---

### *Results & Output*  
- Serial Monitor displays real-time speed (e.g., "Speed: 48 km/h").  
- LEDs activate based on predefined thresholds:  
  - *Green*: Safe speed.  
  - *Yellow*: Approaching limit.  
  - *Red*: Over limit.  

---

### *Expansion Ideas*  
1. Add a buzzer for audible alerts when exceeding limits.  
2. Integrate an OLED display to show live speed.  
3. Implement Bluetooth/WiFi to log speed data.  
4. Use NeoPixel LEDs for dynamic color gradients.  

---

### *Why VSD Squadron Mini?*  
- Dual-core ESP32 for multitasking (sensor interrupts + LED control).  
- Built-in WiFi/Bluetooth for IoT integration.  
- Compact size and GPIO flexibility.  

This project combines embedded programming, sensor interfacing, and real-time feedback, making it ideal for learning IoT basics or creating a practical safety device! 🚴♂🚗💡
