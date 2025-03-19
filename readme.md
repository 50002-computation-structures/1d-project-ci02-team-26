# 1D Project Team 26

[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/vxyPYWbJ)

## Beta CPU Implementation

### ALU and ALU Tester

The ALU strictly follows the guidelines and module design set out in [the project requirements](https://natalieagus.github.io/50002/lab/lab3). 

The ALU tester consists of a manual mode tester and an automatic mode tester, with the ability to transition between the two states.


#### Tester inputs

The DIP switches are arranged in the following order:

```
Leftmost <- ALU fault injection[7:6], ALUFN[5:0] | 
    ALU Input B[31], ALU Input B[7:0]            | 
    ALU Input A[31], ALU Input A[7:0] -> Rightmost
```

- ALU fault injection: allows the user to inject bit flips within the ALU's final output 

The buttons are arranged in the following order:

```
     Start/Pause Clock
N/A     Change Mode     N/A
            N/A
```

- Starts/Pause Clock: Starts or pauses the automated test
- Change Mode: Transitions the mode of operation from manual and automatic and vice versa

#### Tester outputs

The 7 segment display shows the following:

- Current test routine number in **decimals** on the leftmost 2 digits
- Current ALUFN (ALU function) in **hexadecimals** on the rightmost 2 digits

The IO shield LEDs display the following information: 

```
Leftmost <- ALU Output[7], ALU Output [6:0] | 
    ALU Input B[31], ALU Input B[7:0]       | 
        ALU Input A[31], ALU Input A[7:0] -> Rightmost
```

The LEDs at the side displays the following information:

```
ALU Z - zero flag
ALU V - overflow flag
ALU N - negative flag
N/A
N/A
N/A
ALU Fault - lights up when the ALU output does not match the expected input
Clock - clock for the automatic tester, rising edge will load new inputs from ROM, 
        falling edge will engage the automated testing module
```

#### Instructions to use the tester

The ALU tester has 2 primary modes: manual testing and automated testing

Upon power up, the tester is initialized in manual testing mode only.

To use the automated testing feature:

1. Trigger the automated testing mode by pressing the centre button, this will transition it out of manual mode
2. The left 2 digits on the 7 segment should display the decimal number for the test suite, which covers up to 26 test cases, while the right 2 digits should display the current ALUFN in hexadecimal
3. You can pause the clock at any time to inspect the results using the top button
4. You can induce an error in the ALU checker by turning on the `ALU fault injection[7:6]` switches on the leftmost DIP switch, which performs an OR with the ALU's 2 output LSBs.
5. Upon an error in the automated testing routine, the ALU Fault light will turn on and halt at the test case with the error. To continue testing more cases, the user needs to press the top button to ignore the current fault and skip to the next test case.
6. The automated tester can be set back to manual mode at any time by pressing the centre button
