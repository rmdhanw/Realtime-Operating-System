Realtime-Operating-System

This repository will hold multiple projects specially at Realtime Operating Sytem undertaken during my time in university.

STM32 Program for LED Control, Button Input, and UART Communication This project manages various functions on an STM32 microcontroller, including LED control, button reading, ADC value reading from a potentiometer, and UART communication. The program is structured with independent tasks to ensure optimal responsiveness.

Features LED Control: Manage LEDs based on button input and ADC values. Button Reading: Reads the status of a button to determine specific actions. ADC Reading: Reads values from a potentiometer and stores them for use in other tasks. UART Communication: Send and receive data via UART for control and monitoring.

Requirements Hardware: STM32, LED, button, potentiometer Software: STM32CubeIDE or other compatible STM32 development platform

Installation Clone this repository: bash Salin kode git clone https://github.com/rmdhanw/Realtime-Operating-System.git Open the project in STM32CubeIDE. Build and upload the program to the STM32 device.

Task Structure in the Program Here’s an explanation of each task in the program:

Default Task Function: Runs a basic task to keep the system active when no other priority tasks are running. This task simply adds a continuous delay. Interaction: No direct interaction with other tasks.

pickButtonTask Function: Reads the button status with a low logic level. When the button is pressed, this task sets the global variable button1_pressed to 1, with a delay to prevent button debounce. Interaction: The button1_pressed value is used by onLED to control the LED and by dispUARTTask to send the button status over UART.

onLED (LEDTask) Function: Controls two LEDs based on the ADC value (x_val). If the button is pressed (button1_pressed = 1), the LEDs will blink; otherwise, they light up according to the ADC value. Interaction: Depends on getADCTask for x_val values and pickButtonTask for button status. Connects with dispUARTTask to display LED status via UART.

getADCTask Function: Reads the ADC value from a potentiometer and stores it in the x_val variable. Interaction: The x_val value is used by onLED to control the LED and by dispUARTTask for display over UART.

dispUARTTask Function: Manages UART communication. If it receives a 1, it sends the x_val (ADC value) over UART. If it receives a 2, it sends "Hello World!". It also sends "Button 1 pressed" when the button is pressed. Interaction: Depends on the x_val value from getADCTask and button status from pickButtonTask. This task allows user interaction via UART.

Usage LED Control: Press the button to turn the LED on with a blinking pattern or light it up according to the ADC value. ADC Monitoring: View ADC values from the potentiometer via UART. UART Control: Use UART to receive data or send commands (1 for ADC value, 2 for "Hello World!" message).

Contribution Interested in contributing? Fork this repository. Create a new branch (git checkout -b new-feature). Commit your changes (git commit -m 'Add new feature'). Push to the branch (git push origin new-feature). Open a Pull Request.
