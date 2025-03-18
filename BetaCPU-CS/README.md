# Beta CPU Implementation

## ALU and ALU Tester

The ALU strictly follows the guidelines and module design set out in [the project requirements](https://natalieagus.github.io/50002/lab/lab3). 

The ALU tester consists of a manual mode tester and an automatic mode tester, with the ability to transition between the two states.


### Tester inputs

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

### Tester outputs

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
Clock - advancing clock for the automatic tester
```

### Instructions to use the tester

The ALU tester has 2 primary modes: manual testing and automated testing

Upon power up, the tester is initialised in manual testing mode only.

1. Trigger the automated testing mode by pressing the centre button
2. The left 2 digits on the 7 segment should display the decimal number for the test suite, while the right 2 digits should display the current ALUFN in hexadecimal
3. 
