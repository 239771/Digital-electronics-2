# Lab 3: Jesús Borobia Sánchez

Link to your `Digital-electronics-2` GitHub repository:

   [https://github.com/239771/Digital-electronics-2](https://github.com/239771/Digital-electronics-2)


### Data types in C

1. Complete table.

| **Data type** | **Number of bits** | **Range** | **Description** |
| :-: | :-: | :-: | :-- | 
| `uint8_t`  | 8 | 0, 1, ..., 255 | Unsigned 8-bit integer |
| `int8_t`   | 8 | -128...127 | Signed 8-bit integer |
| `uint16_t` | 16 | 0...65535 | Unsigned 16-bit integer |
| `int16_t`  | 16 | -32768...31767 | Signed 16-bit integer |
| `float`    | 32 | -3.4e+38, ..., 3.4e+38 | Single-precision floating-point |
| `void`     | 0 | no-data value | Represents no data value |


### GPIO library

1. In your words, describe the difference between the declaration and the definition of the function in C.
   * Function declaration: It tells the compiler about the name of the function, what kind of value it has to return and the parameters what are needed in that function.Function declarations can be found in .h file.
   * Function definition: It describes what the function does itself with those input parameters and it will return the same type of data that we defined before in the previous declaration. We can define functions in a .c file and we will use them in out main.c file by calling them.

2. Part of the C code listing with syntax highlighting, which toggles LEDs only if push button is pressed. Otherwise, the value of the LEDs does not change. Use function from your GPIO library. Let the push button is connected to port D:

```c
    while (1)
    {
        if(GPIO_read(&DDRD, BTN)==1)
        {
          GPIO_toggle(&PORTB,LED_GREEN);
          GPIO_toggle(&PORTC,LED_RED);
         _delay_ms(BLINK_DELAY);         
        }         
    }
```


### Traffic light

1. Scheme of traffic light application with one red/yellow/green light for cars and one red/green light for pedestrians. Connect AVR device, LEDs, resistors, one push button (for pedestrians), and supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values!

   ![20f2b94c-3408-4ea8-99dd-2bf201937b3c](https://user-images.githubusercontent.com/91123594/136921067-3d1cf32c-86c8-44a3-b699-490e1f441535.jpg)

