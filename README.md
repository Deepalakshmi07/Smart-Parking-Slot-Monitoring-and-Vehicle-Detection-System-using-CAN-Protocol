# Smart-Parking-Slot-Monitoring-and-Vehicle-Detection-System-using-CAN-Protocol

# Objective

- To develop an automatic parking monitoring system using LPC2129 microcontrollers.
- To detect vehicle entry and exit using IR sensors.
- To monitor 6 parking slots and calculate occupied/free slots.
- To display parking status and real-time clock (RTC) information on an LCD.
- To control the parking gate automatically using a servo motor.
- To establish communication between three nodes using the CAN protocol.

# Architecture

           IR Sensors
                 |
                 v
          +-------------+
          |   NODE 2    |
          | IR Detection|
          +-------------+
                 |
              CAN BUS
                 |
                 v
          +-------------+
          |   NODE 1    |
          |   LCD + RTC |
          +-------------+
                 |
              CAN BUS
                 |
                 v
          +-------------+
          |   NODE 3    |
          | Servo Gate  |
          +-------------+

- Node 2: Detects vehicle entry and exit.

- Node 1: Monitors parking slots and displays information.

- Node 3: Controls the entry/exit gate using a servo.

# Components

- LPC2129 Microcontrollers – Used for all three nodes.
- IR Sensors × 2 – Detect vehicle entry and exit.
- 16×4 LCD – Displays parking status and time.
- RTC Module – Provides real-time hours, minutes and seconds.
- Servo Motor – Controls the parking gate.
- CAN Interface – Provides communication between the nodes.
- Power Supply – Provides required power to the system.

# Technologies and Protocols

- Embedded C - Programming the microcontrollers
- CAN Communication - between Node 2, Node 1 and Node 3
- I²C Communication - between Node 1 and RTC
- PWM - Servo motor control
- GPIO - IR sensor interfacing
- LCD - Interface	Parking status display
 
# Project Overview

- The system works using three nodes.

- When a vehicle arrives at the entry, the IR sensor in Node 2 detects it. Node 2 sends an entry message through CAN to Node 1.

- Node 1 receives the message and checks the parking availability. If a slot is available, it increases the occupied slot count and calculates the free slots.

- Free Slots = 6 - Occupied Slots

- Node 1 also reads the current time from the RTC through I²C and displays the parking information on the LCD.

- Then Node 1 sends a gate-control command to Node 3. Node 3 receives the command and rotates the servo from 0° to 90° to open the gate. After 3 seconds, the servo returns to 0° and closes the gate.

- For vehicle exit, the same process occurs using the exit IR sensor, with the occupied slot count decreased and the free slot count increased.

# Overall Flow

Vehicle Detection
       ↓
     Node 2
       ↓
     CAN
       ↓
     Node 1
       ↓
Slot Count + LCD + RTC
       ↓
     CAN
       ↓
     Node 3
       ↓
   Servo Gate


# Applications
- Shopping malls
- Hospitals
- Colleges
- Offices and IT parks
- Airports
- Railway stations
- Residential parking
- Smart cities

# Future Scope
- IoT-based parking monitoring
- Mobile application
- RFID vehicle identification
- Number plate recognition
- Online parking payment
- Cloud-based parking monitoring
