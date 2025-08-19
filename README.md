## Problem Statement
Traffic congestion is a major issue in urban areas, leading to increased travel time, pollution, and difficulties in emergency response. Traditional traffic light systems are fixed-timed and do not adapt to the real-time traffic conditions. This results in inefficient management of vehicles and delays for ambulances and emergency services.  

## Proposed Solution
The proposed system uses an ESP32-CAM to monitor vehicle density and Arduino Uno to control traffic lights. A 1.3" OLED display is used to show the countdown timer for each traffic signal. Additionally, an RF transmitter and receiver module are integrated to provide ambulance priority, ensuring the traffic light turns green when an ambulance is detected.  

## Components Required
- ESP32-CAM module (for vehicle density detection using camera)  
- Arduino Uno (for controlling traffic lights and OLED)  
- FTDI232 programmer (to program ESP32-CAM)  
- 1.3" OLED display (I2C interface, for showing timer)  
- Traffic signal LEDs (Red, Yellow, Green × 4 sets for 4 directions)  
- Resistors (220Ω for LEDs)  
- Breadboard and jumper wires  
- Power supply (5V regulated)  
- RF transmitter module (placed in ambulance)  
- RF receiver module (placed at traffic signal)  

## Working Principle
1. The ESP32-CAM captures real-time images of vehicles at each junction.  
2. Image processing (basic object detection/vehicle count) is used to estimate traffic density.  
3. The Arduino Uno receives density information and adjusts the traffic light timings accordingly.  
4. The 1.3" OLED displays the remaining countdown time for the current green signal.  
5. When an ambulance with an RF transmitter approaches, the RF receiver at the signal detects it.  
6. The system immediately provides green light in the ambulance’s direction, overriding normal operation.  

## Connections
- ESP32-CAM connected to FTDI232 for programming.  
- ESP32-CAM communicates with Arduino Uno via serial (TX/RX).  
- Arduino Uno controls the traffic LEDs (4 sets).  
- 1.3" OLED connected to Arduino Uno using I2C (SDA → A4, SCL → A5).  
- RF receiver connected to Arduino Uno digital input pin.  
- RF transmitter installed in ambulance, powered separately.  

## Additional Feature: Ambulance Priority
- RF transmitter inside the ambulance continuously sends a signal.  
- When the RF receiver at the traffic junction detects this signal, Arduino immediately changes the traffic light of the ambulance’s lane to green.  
- Other directions are switched to red, ensuring ambulance passes safely and quickly.  

## Advantages
- Real-time adaptive traffic light control based on vehicle density.  
- Reduction in congestion and waiting time.  
- Clear visibility of countdown timer for drivers on 1.3" OLED.  
- Ambulance and emergency vehicles get priority, reducing delay in reaching hospitals.  
- Scalable system that can be implemented in smart cities.  

## Future Improvements
- Use of machine learning models for more accurate vehicle detection.  
- Integration with cloud/IoT for centralized monitoring of multiple junctions.  
- Use of GSM/GPS module for live ambulance tracking instead of RF module.  
