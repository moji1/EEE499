---
layout: page
title: FreeRTOS Tutorial-1
---




 
## Introduction 

To use FreeRTOS, we will use a special version that runs in simulation mode in Windows. The simulator is included in the source files and is included in the .exe file that is created during compilation.

We will use Eclipse and the MinGW compiler that is already installed on the lab machines.

The objective of this tutorial is to explore the FreeRTOS code, configure the system and create simple tasks.

## Eclipse Configuration 

To get started, run Eclipse for C ++ Developers . Download the [start code ]({{ "/assets/docs/EmptyFreeRTOSApp.zip" | absolute_url }}), but do not unzip the file.

In Eclipse, go to File> Import> General> Existing Projects into Workspace . Press Next and in the next window select the Select archive file option . Tap Browse ... and navigate to where the start code was downloaded. Tap Finish .

 ![alt text](fig1.png)

You should be able to compile the project into Release. To make sure you can properly start the project, add in the function `main()` before the loop for, the line `printf("Hello World!");` then compile again.

To start the simulator, using the Windows command prompt ( Start> cmd ), navigate to where the .exe file is located (in the directory containing your workspace, for example, `C:\Users\lapointe\cpp-workspace\EmptyFreeRTOSApp\Release`). When you are in the right directory, launch your .exe . It should show Hello World! .

You now have a functional source code and configuration of the FreeRTOS which can be run in simulation mode.  Remember the steps to follow for the lab 3. The fllowing figure shows an overview of the code structures which includes FreeRTOS source code, windows port and configuration file. 

 ![alt text](fig2.png)


## Exploration of FreeRTOS
Referring to the code provided and FreeRTOS book, answer the following questions. You will have to give them to your instructor before the beginning of the lab 3. The answers will be counted in the laboratory 3.


1. What are the possible statuses of a task?
2. In the present configuration, is the OS scheduling cooperative or preemptive?
3. What is the size of the FreeRTOS heap?
4. Are dynamic memory allocation error handling supported?
5. What implementation of `malloc()` and `free()` is used? check heap_* file and explain your answer.
6. What is the Task Control Block for ? How is it defined and where? What information does it contain?
7. Explain how xTaskCreate works.

## Creation of some tasks.
- Create two tasks. One will display "Hello" and the other "World". Observe the behavior of the system. What do you notice?
- Implement examples 1-3 of Chapter 3 of [Mastering the FreeRTOS Real Time Kernel](https://freertos.org/Documentation/161204_Mastering_the_FreeRTOS_Real_Time_Kernel-A_Hands-On_Tutorial_Guide.pdf) 

Note: You must use fflush(stdout) after using printf().