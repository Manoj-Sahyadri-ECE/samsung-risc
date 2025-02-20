Line follower robot using VSDsquadronmini

![image](https://github.com/user-attachments/assets/a1706305-4c25-46e1-a812-57f36f5a286d)

A line follower robot is an autonomous robot designed to follow a predefined path, usually marked by a visible line or track, such as a black line on a white surface (or vice versa). These robots are equipped with sensors that enable them to detect the line and adjust their movement to stay on course. The robot continuously reads sensor inputs and makes decisions to ensure it follows the path accurately.
Key Components:
1. Sensors: 
   - 3 IR sensors (left, center, right) to detect the line’s position.
   - The robot moves forward if the center sensor detects the line and adjusts based on the other sensors.
   
2. Motor Control:
   - Uses an H-bridge motor driver (like L293D) to control motor 
speed and direction.
   - Motors move the robot based on sensor inputs to align with the line.
3. Decision Logic:
   - Forward if the center sensor detects the line.
   - Turn right if the left sensor detects the line.
   - Turn left if the right sensor detects the line.
   - If no sensor detects the line, it stops or searches for the line.

 Components:
- 3 IR sensors, L293D motor driver, 2 motors, and VSDSquadronmini controller.

 Pin Configuration:
- VCC: 5V
- GND: GND
- IR Sensors: PD5 (left), PD6 (center), PD7 (right)
- Motor Driver Pins: PD1, PD2, PD3, PD4
- Power: 12V as Vin.

This robot is ideal for robotics competitions, educational projects, and industrial automation tasks.

