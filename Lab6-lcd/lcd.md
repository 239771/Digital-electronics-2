# Lab 6: Jesús Borobia Sánchez
Link to this file in your GitHub repository:

  [https://github.com/239771/Digital-electronics-2](https://github.com/239771/Digital-electronics-2)


### LCD display module

1. In your words, describe what ASCII table is.
   * ASCII table: as it´s own name describes, its a table in which we can find equivalents between our language characters and it´s translation in different machine languages as binary. 
   * In that table we can also see other translations for example hexa. For each character we have an unique ASCII code.

2. (Hand-drawn) picture of time signals between ATmega328P and LCD keypad shield (HD44780 driver) when transmitting three character data `De2`.
 
 ![lab6im1](https://user-images.githubusercontent.com/91123594/139904558-a859736f-d73b-4dd9-9a5c-9a6a4ee7d282.png)
  
3. 
 
 ![lab6im2](https://user-images.githubusercontent.com/91123594/139904608-d6862edc-3530-4fcf-b594-6880e03c342d.png)


### Stopwatch

1. Flowchart figure for `TIMER2_OVF_vect` interrupt service routine which overflows every 16&nbsp;ms but it updates the stopwatch LCD approximately every 100&nbsp;ms (6 x 16&nbsp;ms = 100&nbsp;ms). Display tenths of a second and seconds `00:seconds.tenths`. Let the stopwatch counts from `00:00.0` to `00:59.9` and then starts again. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

   ![your figure]()


### Custom characters

1. Code listing of two custom character definition. Always use syntax highlighting and meaningful comments:

```c
/* Variables ---------------------------------------------------------*/
// Custom character definition
uint8_t customChar[16] = {
   
    0b01110,    //Human form
    0b01110,
    0b10001,
    0b01100,
    0b01100,
    0b10001,
    0b10001,
    0b10001,
    
    0b00000,    //Heart form
    0b01010,
    0b11111,
    0b11111,
    0b11111,
    0b01110,
    0b00100,
    0b00000

};
```


### Kitchen alarm

Consider a kitchen alarm with an LCD, one LED and three push buttons: start, +1 minute, -1 minute. Use the +1/-1 minute buttons to increment/decrement the timer value. After pressing the Start button, the countdown starts. The countdown value is shown on the display in the form of mm.ss (minutes.seconds). At the end of the countdown, the LED will start blinking.

1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.

  ![circuitlab6](https://user-images.githubusercontent.com/91123594/139901736-e080a560-5674-465e-b6ff-3df4a3d5e7e7.png)
