# Lab 1: Borobia

Link to your `Digital-electronics-2` GitHub repository:

   [https://github.com/...](https://github.com/...)


### Blink example

1. What is the meaning of the following binary operators in C?
   * `|`, Logic operation OR
   * `&`, Logic operation AND
   * `^`, Logic operation XOR
   * `~`, One´s complement operation
   * `<<`, Left shifting operation
   * `>>`, Right shifting operation

2. Complete truth table with operators: `|`, `&`, `^`, `~`

| **b** | **a** |**b or a** | **b and a** | **b xor a** | **not b** |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 |


### Morse code

1. Listing of C code with syntax highlighting which repeats one "dot" and one "comma" (BTW, in Morse code it is letter `A`) on a LED:

```c
/* This code makes a LED blinking and showing letter A according to Morse´s code*/

/* Defines -----------------------------------------------------------*/
#define LED_GREEN  PB5     // AVR pin where green LED is connected
#define DOT_DELAY 500       //Delay of dot in Morse
#define COMMA_DELAY 1500    //Delay of comma in Morse--3 times a dot aprox
#ifndef F_CPU
#define F_CPU 16000000     // CPU frequency in Hz required for delay
#endif

/* Includes ----------------------------------------------------------*/
#include <util/delay.h>     // Functions for busy-wait delay loops
#include <avr/io.h>         // AVR device-specific IO definitions

int main(void)
{
    // Green LED at port B
    // Set pin as output in Data Direction Register...
    DDRB = DDRB | (1<<LED_GREEN);
    // ...and turn LED off in Data Register
    PORTB = PORTB & ~(1<<LED_GREEN);

    // Infinite loop
    while (1)
    {   //A in Morse code is dot+comma
        PORTB=PORTB^(1<<LED_GREEN); //Turn on LED
        _delay_ms(DOT_DELAY);  // Pause for dot´s delay
        PORTB = PORTB & ~(1<<LED_GREEN); //Turn off LED
        _delay_ms(DOT_DELAY);  // In Morse we wait aproximetly 1 dot time between symbols
         PORTB=PORTB^(1<<LED_GREEN); 
        _delay_ms(COMMA_DELAY); //Pause for comma´s delay
        PORTB = PORTB & ~(1<<LED_GREEN);     
    }

    // Will never reach this
    return 0;
}
```


2. Scheme of Morse code application, i.e. connection of AVR device, LED, resistor, and supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values!

   ![your figure]()
