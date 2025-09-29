---
layout: post
title: Task Scheduler
permalink: /proj11
---

Processor: ARM Cortex M4 
MCU: STM32F4 Discovery Board

In this project, I wrote a task scheduler that schedules multiple user tasks in a round-robin fashion by carrying out a context switch operation.
The user tasks in this case were toggling LED lights on and off on the board.

I also was able to build and run this executable using GNU tools, which was so cool! I am not the biggest fan of the STM32CubeIDE.

In order to successfully complete this, I learned how to:

1. Create stack areas for the scheduler and user tasks within RAM.

2. Perform context switching via context saving and context retrieving during the PendSV exception.

When performing a context switch, the running task must be saved, and the next task's state must be retrieved.
The processor performs stacking and unstacking whenever an exception occurs, saving and retrieving some information already.
On top of the registers saved during the stacking operation, I saved other registers required in another stack frame to perserve all necessary data.
To move onto the next task, I moved the stack pointer to the next task's saved PC.

3. Use the SysTick Timer to schedule context switching to occur every 1ms. 

When the SysTick Timer went off, the PendSV handler would be set to a pending state.
If no other interrupts occur, the PendSV handler would execute the context switch.

4. Use PSP for the stack pointer in thread mode (the user tasks) and MSP for the stack pointer in handler mode. 

Through in-line assembly instructions, I learned how to manipulate the values of PSP and MSP.

5. Preserve the correct address in the Link Register (LR).

Oftentimes, I would call other functions in naked functions to do something to PSP or MSP.
It was important that the LR be pushed onto the stack before and retrieved after calling another function to ensure that the correct return address was saved.
I also learned how the EXE_RETURN value is stored in LR during exceptions, how it controls the exit of an exception, and the various values it could hold.

6. Don't waste CPU clock cycles. Use a hardware delay (via the SysTick Timer) and add state to tasks to ensure that the scheduler only schedules tasks that are ready to be scheduled.

This was achieved by having two states for tasks, ready or blocked, which was evaluated every time the SysTick timer exception would occur.
It was also important to write a good algorithm to determine what task could be scheduled next based on these states; if all tasks were blocked, an idle task would run.

7. Addressing potential race conditions in accessing global variables used by both thread and handler code.

As a solution to this, I simply disabled and re-enabled interrupts every time a global variable was accessed.
However, I understand that this application was incredibly simple. This is probably not the best solution in a time critical application, where every second matters.

8. Write a microcontroller startup file for STM32F4 MCU.

I learned how to initialize the vector table for this MCU, and how to use a "weak" function to my advantage in this process, alongside giving a function an "alias."
One can simply create a Default Handler as an alias for all the handler functions instead of implementing 98 of them (which may not even be used), and let the programmer override the default with the keyword "weak."
I also learned the difference between data that belongs in ".data" vs ".bss," and wrote code to move the ".data" section from Flash memory to SRAM during startup.

9. Write a linker script file from scratch and understand section placements.

I learned that a .o file is a relocatable object file. The linker script takes this file, and then relocates all of the addresses accordingly to the MCU address map.
With the linker script, we can create one big executable from mulitple object files.

10. Load final executable on the target using OpenOCD and GDB client.

I learned how to connect the board with OpenOCD and use GDB to debug. I gained a deeper understanding of how these tools worked together.

11. Use a Makefile

I wrote a Makefile for all the build commands I had to run, and it was so great to use.
From this, I also learned how to use different spec files for semihosting and different standard C libraries.

Overall, I felt like I truly learned so much from this project. I now have a much deeper understanding of the build process of a program, and processor exceptions.
I appreciated the stack memory manipulation, and sharpening my ARM assembly reading skills.

Code can be found [here](https://github.com/ivy-phngyn/task-scheduler)

