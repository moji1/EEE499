---
layout: page
title: Lab4
---

## Objectives


This lab is an introduction to develop a real-time software based on UML-RT language. You will design a simple digital watch which will help you to understand the UML-RT concepts effectively by applying them in practice. The lab covers the main concepts of UML-RT (structural modeling, behavioral modeling, Timers, and code generation).

Show results of your work to your instructor weekly. 

## Digital Watch Description 

The functionality of the watch is same as [Lab3]({{ "labssrc/lab3/lab3.html" | absolute_url }}). 

### Non-functional Requirements
Download [this papyrus project]({{ "/assets/docs/DigitalWatch-UMLRT.zip" | absolute_url }}) and use it as initial project for your solution. You can add a new capsule to the project but the existing capsules  in the model which are explained below must be part of your solution. Do not touch the `DigitalWatch.controllers` file which is located in the project's root. 

1. **Core** capsule should provide the core services and controls the watch. 
2. **TimeTracker** capsule should track the progress of time.
3. **Stopwatch** should provide the stopwatch services. 
4. **Display** capsule works as the gatekeeper for showing a message on display. None of the capsules can write directly to the command line. All requests should be sent to *Display* capsule. 
5. **Readkey** capsule manages reading the keys and passes them to the *Core* task.
6. **DigitalWatch** capsule the top capsule.
7. **Alarm** capsule manage the alarm functionality.

8. There is no requirement for resource management.

9. The time resolution for the watch should be 500ms.

10. The stopwatch's counter resolution should be 200ms.

11. The watch must be displayed in the format `hh:mm:ss` and updates every second.

12. The stopwatch must be displayed in the format `hh:mm:ss:ms` where ms is the milliseconds. 

### Parts 

Follow the iterative process as explaied in [Lab3]({{ "labssrc/lab3/lab3.html" | absolute_url }}).


### Hints

Here are some hints which may be helpful during implementation:


1. Use the following code for reading a key without waiting for fo the end of line character. 

    ```c++
    struct termios t; 
    tcgetattr(STDIN_FILENO, &t); 
    t.c_lflag &= ~ICANON; 
    tcsetattr(STDIN_FILENO, TCSANOW, &t); 
    char key= std::cin.get();
    ``` 


2. for beep use `printf("\a")`


## Lab report

Your lab report should include a cover page, a brief introduction, discussion, and conclusion.

Your discussion should explain your design in detail. 


Use the following format for your [report]({{ "/assets/docs/lab-report.docx" | absolute_url }}).


### Submission

You must submit your lab report in *PDF* format and your code by e-mail in a *.zip* file.