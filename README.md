# Microbull Proposal

## Overview

The Microbull Micromouse will be a Rasberry Pi based mouse that will use Python based ROS2 to interface with four dc motors connected to omniwheels and use four ultrasonic sensors for sensing. The mouse will not need to take any turns, as its omniwheel design will allow it to directly move in any desired direction. Communication with the Pi and the ultrasonic sensors will take place over GPIO pins. Communication with the motors will also take place over GPIO pins, and the encoder feedback will also be received over GPIO. There will be two seperate circuits, one to power the Pi and 3.3V logic and another that will power motors at 6VDC. We anticipate the the mouse will be able to run for anout 10 minutes straight on a full battery charge. 

### Software Plan
The Microbull will be programmed using Python 3 and ROS2. We will be using ROS2 controller libraries to interface with the motors. There will be ROS2 nodes for: the maze-solving algorithm (which will be using floodfill), the position-determining algorithm, and the motor-control algorithm. The nodes will communicate over the following ROS topics: current position, requested position, drive output, and encoder feedback. 

The __Node__ Position Determiner will: output to __Topic__ `current position`, output to __Topic__ `drive output`, listen to __Topic__ `requested position`, listen to __Topic__ `encoder feedback`. 

The __Node__ Motor Driver will: output to __Topic__ `encoder feedback`, listen to __Topic__ `drive output`. 

The __Node__ Flood Fill will: output to __Topic__ `requested position`, listen to __Topic__ `current position`. 

### Hardware Plan
This should be a more detailed explanation of how your hardware will work. This should include the electrical requirements of all the individual components of your system and how those requirements will be managed. This should also include a detailed explanation of the hardware components of your system and how they will interact with each other. This should include a detailed explanation of the sensors you will be using, how they work, and how you will be using them to complete your task. This should also include specifications of your components, including the voltage/current ranges they support as well as their physical dimensions (when applicable).

## Flowchart of System Design

![Flowchart of System Design](images/MicroBullProposalFlowchart.png)

## Parts and Costs

### Purchases

| Item Name w/Link | Cost per Unit | # of Units | Total Cost |
| ---- | ---------------- | ---- | ---------------- |
| [Rasberry Pi 4B 4GB](https://www.digikey.com/en/products/detail/raspberry-pi/SC0194-9/10258781) | $55.00 | 1 | $55.00 |
| [Ultrasonic Distance Sensor - 3V or 5V - HC-SR04 compatible - RCWL-1601](https://www.adafruit.com/product/4007) | $3.95 | 4 | $15.80 |
| [USB Li-Ion Power Bank with 2 x 5V Outputs @ 2.1A - 5000mAh](https://www.adafruit.com/product/4288) | $26.95 | 1 | $26.95 |
| [DC Gearbox Motor - "TT Motor" - 200RPM - 3 to 6VDC](https://www.adafruit.com/product/3777?gad_source=1) | $2.95 | 4 | $11.80 |
| [Adafruit DRV8833 DC/Stepper Motor Driver Breakout Board](https://www.adafruit.com/product/3297) | $5.95 | 2 | $11.90 |
| | | **Total** | **$** |

### Custom Creation

1. Wheels - 3D printed.
3. Chassis - 3D printed.
4. Compute Casing for Raspberry Pi and battery - 3D printed.

### Parts on Hand

1. Wires
2. Breadboard

## 3D Model

Our model consists of a basic square chassis, four motors attached to gearboxes, two H-Bridge Stepper Motor Drivers,
a Raspberry Pi 4, an Adafruit battery bank, four ultrasonic sensors, and four wheels. The wheels on the model only represent the size and occupation area of the real wheels which will be mecanum wheels.

Isometric View:
![3D_Model](images/3D_Model.png)

Top-Down View:
![3D_Model_Top](images/3D_Model_Top.png)

## Teammates and Responsibilities

### Eric 
Will create the ROS2 software setup. Will program the sensing, control, and maze-solving algorithms. Will test the program. 

### Ben   
Will assist in python programming for the software stack including software-hardware integratino with the motors and encoders. Will manage the power supply circuitry and the motor control circuitry. Responsible for ensuring that the Arduino and motor controllers are both properly powered from the battery but are on separate circuits with the proper voltages and currents. 

### Jared
Responsible for 3D modelling and 3D printing of parts including the omniwheels, the chassis, and the holders for the Pi and power pack. Responsible for wiring and manging circuitry. 

### Margaret
Responsible for wiring and manging circuitry. Will manage the power supply circuitry and the motor control circuitry. Responsible for ensuring that the Arduino and motor controllers are both properly powered from the battery but are on separate circuits with the proper voltages and currents. 

## Milestones

### Milestone Set 1: 11/8/23

* Get GPIO output from the pi to light up LEDs on a breadboard. 
* Get GPIO input from the pi to read button presses on a button.
* Get GPIO input from the pi to read sensor data from the ultrasonic sensors.
* Initial 3D Model for chassis completed.

### Milestone Set 2: 11/22/23
* Get the algorithm working in simulation. 
* Positioning algorithm can properly identify where mouse is within a single maze cell.
* Can make the motors spin from the battery.

### Milestone Set 3: 11/29/23
* Pi can make the motors spin in both directions. 
* Pi can read sensor data and calculate the position of the mouse when moving thorugh corridors of the maze. 
* Firmware can control the motors and receive input from encoders to properly move the mouse as instructed.
* Mouse can move forward, backward, to the left, and to the right. 


### Milestone Set 4: 1/10/24
* Mouse can move in a straight line and stop when it reaches an obstacle.
* Mouse can turn 90 degrees when told to by the algorithm.
* Mouse can move for 10 minutes straight. 
* Mouse can execute different algorithms based on user inputs from physical buttons on the mouse. 
* Flood fill working on Rasberry Pi in firmware and works in simulation. 

### Milestone Set 5: 1/24/24
* Mouse can move through a maze randomly without hitting walls.

### Milestone Set 6: 2/7/24
* Mouse can solve the maze. 



