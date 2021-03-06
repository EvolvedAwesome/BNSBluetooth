# BNS Bluetooth Library for RobotC 4.27

This is a small library for being able to reprogram an HC05 Bluetooth Module using the Cortex.  
This reduces the need for having an arduino or usb->uart dongle to reprogram the module.  
Reprogramming allows you to change the bluetooth name and uart baudrate/settings from the default state via AT commands.  See atDemo.c for using the AT commands. 

This library also gives examples for how to send sensor data over the HC05 bluetooth dongle.  See bluetoothDemo.c and IMEBluetoothDemo.c.

Includes:
  * Functions and examples for sending and recieving commands over UART
  * AT Commands for reprogramming HC05 bluetooth modules.  
  
Connecting a HC05 to a Vex Cortex is not difficult at all.  
The HC05 module commonly found online can be powered from a 5V source, and the TX/RX pins run at 3.3V, so no conversion is necessary from the Cortex to the module.
For reprogramming it, connect the "key" pin to 5V before powering the cortex. (Disclaimer: this could potentionally damage your device as the key pin is not made to run at 5V.  Use a voltage divider down to 3.3V if you want to be safe). 

Here is the a diagram showing how to connect one model of HC-05 module to the cortex:
![Uart Connection Diagram](http://www.vexforum.com/index.php/attachment/56464da80f24e_Pinout_HC05.jpg)

The black wire is ground, the red wire 5V.  The Green/Yellow wires are TX/RX wires which transmits the uart data (These should go from TX to RX port).  The blue wire is the "key" which, when when set to 3.3V/5V, puts the bluetooth dongle into the "reprogrammable state". On some models of the HC-05 that feature an 'en' pin where the key is featured here, you may have to provide 3.3V/5V to pin34 on the side (the top right-hand pin next to the antenna).

For other advice or support, head over to the [vexforum post](http://www.vexforum.com/index.php/14783-bnsbluetooth-robotc-library-for-the-hc-05/0).

Functions Cheatsheet: 
 * bnsSerialSend(UART1, "Hello Vex!"); // Sends a string over UART1
 * bnsSerialRead(UART1, someString, 100, 1000); // Reads a string over UART1 without a 1second timeout
 * bnsATTestConnection(UART1); // Returns true if there is a connection between the cortex and HC05 over UART1
 * bnsATGetName(UART1); // Prints the name of the HC05 module to the debug stream
 * bnsATSetName(UART1, "Team BNS"); // Sets the name of the HC05 module which.
 * ... and more AT commmands. 
