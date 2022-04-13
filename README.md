# Industrial Control Trainer (ICT3) Project

The Industrial Control Trainer represents an industrial assembly system that allows the study of control methods used in product assembly and inspection in a manufacturing process. Various industrial sensors and the methods, in which they can be used, are studied. The Sensors and actuators are used to sort components, assemble them and test for correct assembly followed by acceptance or rejection. 


https://user-images.githubusercontent.com/73859429/163284797-69b0d060-c132-475e-b125-c04908e3a534.mp4
![ICT Flow Chart](https://user-images.githubusercontent.com/73859429/163288216-c8e3f9c7-434b-46be-87a2-d0cb0649c92e.png)


## Components that work in the ICT implementation:

	1. Real-time snapshot indicating sensors and actuators are active/deactivated at all times
	2. Number of widgets processed during the operation
	3. The efficiency of the system
	4. A means of system recovery in case of power loss
	5. Max hopper count of 5

1) There are boolean buttons and LEDs representing each sensor and actuator used within the ICT.
   These values are changed depending on user input and sensors within the ICT sensing
   widgets. Each boolean indicator has a form a logic to set the ICT in motion.

2) Number of widgets processed during operation are counted by the "Top Thing" sensor, as every 
   object passing through the assembly line of the ICT is passed through the Top Thing sensor.

3) The efficiency of the system is calculated within the code via the ratio between the number of
   widgets assembled divided by the total number of widgets processed during operation. This value
   present within the user interface is better considered when all widgets have passed through the 
   ICT and have either been rejected or assembled.

4) The systems is recoverable in the case of power loss in the sense that the Queue and Number
   indicators of our system are saved over time and can be opened within the user interface
   or in a .txt file after closing LabView

5) The max hopper count is set to 5 as the hopper is completely full at that point. This was 
   determined based on the overall count produced by the top solenoid actuating. The dropper count
   incremented as top solenoid is active, and decremented as the Dropper sensor is active. 
   The increment/decrement of count is based off rising edges as well as event cases for said sensors

## Components that don't work in the ICT implementation:

	1. Saving of Boolean values for status detection
	2. Pause/Unpause Button

1) The saving of Boolean values, such as status for a variety of sensors is not implemented

2) The Pause/Unpause button is not implemented

# What can be improved in the implementation?

If some more time was provided the missing components of the program (Saving of Boolean Values & Pause button)
would have been completed. Both components however are quite simple to implement. 

The saving and reading of Boolean values is similar to that of the queue and numbers we have implemented 
within the code, and would be used for saving the values of sensor status LED indicators. 

For the "Pause button", an easy way to execute this implementation would be by putting the boolean for this 
button within a case structure. This case structure would be relying on the value of a status for the "Start" 
sensor. When the "Start" status is true, the pause button may be activated/deactivated, when the "Stop" sensor
is activated, the Start status is made false and the system stops.

As for improving the current design of the implementation, there are many improvements that can be made.

For instance:

 * Adjusting and working on the queue code to make it more accurate for moments when multiple components are lined up back to back for queuing.
 	* Also have the queue determine whether or not a non-assembled widget passing is a plastic 
 	  or metal, to create a more clear understanding when the rejection process occurs.

* Improve or add more logic that applies for the rotary as some errors may occur

* Have the belt motor stop when there are no plastics widgets present within the dropper. This 
  will increase efficiency as metal widgets will wait at the beginning of the belt motor
  until there are plastics present, so more assemblies can be made.

* Implement each component in its own while loop and add wait timers as time delays act in a
  isolated manner when applied over the course of multiple while loops. In the current state
  of the code, falling and rising edges allow for the program to work without any time delay.

