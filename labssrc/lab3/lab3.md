---
layout: page
title: Lab3
---

## Objectives


This lab is an introduction to develop a real-time software based on FreeRTOS. You will design a simple digital watch which will help you to understand the FreeRTOS concepts effectively by applying them in practice. The lab covers the main concepts of FreeRTOS (task management, timer, inter-task communication, and resource management).

In the first part of the lab, you will learn how to create a FreeRTOS application, define tasks and configure them. By configuring, we mean to specify the tasks' priority, period and etc. After defining the tasks, in the next three parts which are intertwined, (1) you will learn how to defines and use timers, (2) setup the communication between tasks using queues, and (3) use resource management techniques to manage the available resources and synchronize between tasks. 

Following, first, we describe the functional and non-functional requirements of the watch and then present a brief guide for each part. You may try different ways to accomplish this lab as far as the final solution addresses the requirements. 

Show results of your work to your instructor weekly. 

## Digital Watch Description 

### Environment
You need to use FreeRTOS windows simulator to develop your solution. Since you do not use real hardware, you will use the console (Windows cmd) as the watch display and use the keys (`0`,`1`,`2`,`3`) to provide inputs for your watch. Please note you can also use Arduino Board if you are interested. 


### Functional Requirements of the Digital Watch
The watch should provide the following functionalities 

The digital watch should provide the following functionalities 

1. **Displaying Time:** When the watch starts, it sets the time to 00:00:00. It then tracks the progress of time and displays it on the watch display (the command line). You cannot use the system API to read the system time and the watch should have a periodic task to track the progress of time.

2. **Stopwatch:** Pressing `0` toggles between the stopwatch mode and the normal mode. When the watch switches to the stopwatch mode, the stopwatch value should be shown on the display.  Pressing `1` starts the stopwatch and pressing again stops it. Pressing `2` resets the stopwatch. 

3. **Alarm:** Pressing `3`, allows the user to set an alarm by entering a time (hour and minutes). Obviously, the watch should start beeping when the alarms time is reached. The simplest way to implement the alarm is to use a software timer.


### Non-functional Requirements
There are many ways to implement the functional requirements, however your solution should include the following features.

1. Your solution should include 5 tasks. 
	1. **Core** task which provides the core services and controls the watch. 
	2. **TimeTracker** task which tracks the progress of time.
	3. **Stopwatch** task which provides the stopwatch services. 
	4. **Display** task that works as the gatekeeper for showing message on the display. None of the tasks can write directly to the command line. All requests should be sent to *Display* task. 
	5. **Read-key** task which manages reading the keys and passing them to the *Core* task.

2. The display, the keyboard, the time, and the stopwatch counter are shared resources that must be accessed exclusively. Use proper mutual exclusion solution when accessing these resources. 

3. The time resolution for the watch should be 500ms.

4. The stopwatch's counter resolution should be 200ms.

5. The watch must be displayed in the format `hh:mm:ss` and uodates every second.

6. The stopwatch must be displayed in the format `hh:mm:ss:ms` where ms are the milliseconds. 

7. Follow the naming convention of FreeRTOS.


### Hints

Here are some hints which may be helpful during implementation:

1. Do not try to implement all features of the watch at once. We recommend, first, develop a simple watch that only shows times, then add the stopwatch and alarm functionalities.  
2. Use `getch()` and `scanf()` functions to read keys and values accordingly. Remember to `fflush(stdin)` after each use of them. To use `getch()` you have to include `conio.h`.
3. Use `printf` for printing. Remember to `fflush(stdout)` after each use.
4. Use `Beep()` function for beeping which is required for the alarm service. You need to include `Windows.h`. Refer to the following [link](https://msdn.microsoft.com/en-us/library/windows/desktop/ms679277%28v=vs.85%29.aspx) for more detail. 
5. Required information to implement this lab is covered in the course material. You may also refer to the FreeRTOS books available [here](https://freertos.org/Documentation/RTOS_book.html).
6. For the sake of clarification, we will demo a sample digital watch during the lab session. 


## Lab report

Your lab report should include a cover page, a brief introduction, discussion and conclusion.

Your discussion should explain your design in detail (e.g., tasks configuration, how the priority and period of tasks are defined, how resources are shared and ...)  and presents the behavior of each task using a state machine diagram. 


Use the following format for your [report]({{ "/assets/docs/lab-report.docx" | absolute_url }}).


### Submission

You must submit your lab report in *PDF* format and your code by e-mail in a *.zip* file.