# Final project proposal

- [x] I have reviewed the project guidelines.
- [x] I will be working alone on this project.
- [x] No significant portion of this project will be (or has been) used in other course work.

## Embedded System Description

  The goal of this project is to track where a laser pointer is pointed at on a section of a wall and track where the point is using a separate laser attached to a turret on the camera housing. When the device is powered up, the laser will move through a set of predetermined patterns to ensure functionality. After this has been completed, the keypad will allow the user to enable tracking. From this point until the tracking is turned off, if a laser is pointed at a spot inside the designated area of wall, the turret will point its own laser at the same location on the wall. 

  The first input to the system would be a camera, providing frames to be analyzed. The MSP would find the brightest spot on the frame, where the laser is pointing, and decide on the actions needed to point its laser at that spot. There would be two DC motors controlling the laser turret, one for the x axis and one for the y. These two motors would provide inputs of their current position to the MSP. The outputs of the system would be motor controlling signals to adjust where the laser is pointing.

## Hardware Setup

  Initial research into using an MSP430 for video processing implies that a frame buffer is needed for the MSP to be able to properly analyze video. There is a version of the ov7670 camera that has an integrated FIFO video buffer, which would likely prove beneficial for this project. Two DC motors are required for the x and y axis. MSP devices cannot directly interface with a DC motor, so a motor driver IC will be required. The L293D chip will work for this as it can control several motors simultaneously.
  
  The design of the turret will have the camera mounted at the bottom of the tower along with the MSP’s and the L293D. Directly above them will be a DC motor pointed up, along with support columns capable of helping hold up the weight of the above parts but not limit rotation. Connected to the output of the first motor will be a small platform with another motor and a laser on it. The laser will be mounted on bearings allowing it to rotate vertically, with a wheel attached to the bearing rod. The motor will have a similar wheel on its output, and a band will connect the two, allowing for control of the laser’s elevation. 

## Software overview

  The MSP430FR2355 will read in a frame from the camera via uart, and will determine the brightest pixel on the frame. The MSP will then use its lasers current position and the location of the brightest position to calculate how it needs to change where it is pointing. These change values (positive or negative int for x and y) are then transmitted via I2C to a MSP430FR2310. The MSP430FR2310 controls the DC motors to point at the correct location. 
## Testing Procedure

  First, I will work to get the camera to send an image to my computer to verify that it works. The turret can be tested by manually providing I2C transmissions via an Analog Discovery 2. Any projector screen should work for a demo. 
  
  Getting the camera to differentiate between the user’s laser and the turret laser will be a challenge, but there are several possible solutions to this. First, different colors could be used so that the camera can differentiate between them. Secondly, an infrared laser could be used as the turret laser so that there will only be one laser in the visible spectrum in the field of view. However, this second option will require the use of an infrared camera for viewing the tracking.


## Prescaler

Desired Prescaler level: 

- [ ] 100%
- [x] 95% 
- [ ] 90% 
- [ ] 85% 
- [ ] 80% 
- [ ] 75% 

### Prescalar requirements 

**Outline how you meet the requirements for your desired prescalar level**

**The inputs to the system will be:**
1.  Camera for frames
2.  DC motor one
3.  DC motor two

**The outputs of the system will be:**
1.   DC motor one
2.   DC motor two

**The project objective is**

Build a turret that can accuratly point a laser at a specific location

**The new hardware or software modules are:**
1. ov7670 camera
2. DC motors
3. L293D motor controller


The Master will be responsible for:

Finding the laser spot in the camera, telling where to move motors.

The Slave(s) will be responsible for:

Move the turret with DC motors.



### Argument for Desired Prescaler

The requirements for this prescaler are met as this proposal has 3 inputs, the camera and the two DC motors, and 2 outputs, the two DC motors. The objective of this project is to design a working tracking system, and it will implement new hardware and software not used in either EELE 371 or EELE 465. 
