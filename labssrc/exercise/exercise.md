---
layout: page
title: Task Profiling  
---




 
## Introduction 
As we discussed during the course, there are two approaches to measure the task execution time. (1) static analysis (2) task profiling.
During this exercise, you will apply task profiling in the context of FreeRTOS and digital watch application. After calculation of execution time for all tasks, you will perform the schedulability analysis for your digital watch application and verify if any task misses its deadline.  


## Profiling of Digital watch 
The primary goal of the profiling is to execute the application in many scenarios for different input as much as possible and collect the execution time for each scenario. After collecting data, analyze the data and calculate the worst-case execution time for each task. To profile the digital watch application follow these steps:

 1- Replace the read-key task with another task that generates different inputs for the watch. You need to implement an enumeration technique that generates all possible input for the digital watch. 

 2-  instrument the task function to log the tick count and beginning and end of each task. This can be done using `xTaskGetTickCount` function. 
 
 3-  After collecting the data, calculate worst-case execution time for each task.


## Schedulability analysis
extract a task model of your digital watch solution and perform the schedulability analysis using response time analysis.






## Submission
Submit your solution as part of the Lab4.
