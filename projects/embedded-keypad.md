---
layout: post
title: Embedded Keypad Driver
permalink: /proj07
---

I designed and implemented a bare-metal driver for a 4x4 matrix keypad on an STM32 microcontroller.
A row-column scanning technique was used to efficiently detect keypresses in the absence of an RTOS.
I also utilized software debouncing logic to ensure accurate key detection and reduce false triggers.

Overall, it was so fun getting to play around with registers and pointers. Highly appreciated the power of C through this small mini-project!
I also learned how to make code more readable by utilizing structs and macros :D

Code can be found [here](https://github.com/ivyngu/embedded-foundations)

