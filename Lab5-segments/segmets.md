# Lab 5: YOUR_FIRSTNAME FAMILYNAME

Link to your `Digital-electronics-2` GitHub repository:

   [https://github.com/239771/Digital-electronics-2](https://github.com/239771/Digital-electronics-2)


### 7-segment library

1. In your words, describe the difference between Common Cathode and Common Anode 7-segment display.
   * CC SSD: All the LEDS cathodes will be connected in the same terminal, which is GND, so the way to turn those LEDS on is to apply some VCC voltage...LEDS will be active in high level.
   * CA SSD: In this case all the LEDS anodes will be connected also in the same terminal but now this will be a VCC terminal so in order to turn them on we must apply 0V...LEDS will be active in low level

2. Code listing with syntax highlighting of two interrupt service routines (`TIMER1_OVF_vect`, `TIMER0_OVF_vect`) from counter application with at least two digits, ie. values from 00 to 59:

```c
/**********************************************************************
 * Function: Timer/Counter1 overflow interrupt
 * Purpose:  Increment counter value from 00 to 59.
 **********************************************************************/
ISR(TIMER1_OVF_vect)
{
    if(cnt1==9){ //Overflow for units equals 9, adding +1 in the second digit to reach tens
      cnt1==0;
      cnt2++;
    }
    else{       //No overflow means just keep increasing units
      cnt1++;
    }
    
    if(cnt2==6){     //Overflow for the limit of our counter (60)
      cnt2==0;
      cnt1==0;
    }
}
```

```c
/**********************************************************************
 * Function: Timer/Counter0 overflow interrupt
 * Purpose:  Display tens and units of a counter at SSD.
 **********************************************************************/
ISR(TIMER0_OVF_vect)
{
    static uint8_t pos = 0;      //In every interrupt it will change the position of the shown display
    if(pos==0){
     SEG_update_shift_regs(counter1,0);  
     pos=1; //Change position 
    }
    
    else{
     SEG_update_shift_regs(counter2,1);   
     pos=0;
    }
  
}
```

3. Flowchart figure for function `SEG_clk_2us()` which generates one clock period on `SEG_CLK` pin with a duration of 2&nbsp;us. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

   
![IMG-20211026-WA0006](https://user-images.githubusercontent.com/91123594/138903731-2ed1957d-2ca4-49b6-b4a0-0e8aeca07af2.jpg)

### Kitchen alarm

Consider a kitchen alarm with a 7-segment display, one LED and three push buttons: start, +1 minute, -1 minute. Use the +1/-1 minute buttons to increment/decrement the timer value. After pressing the Start button, the countdown starts. The countdown value is shown on the display in the form of mm.ss (minutes.seconds). At the end of the countdown, the LED will start blinking.

1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.

![lab5 draw](https://user-images.githubusercontent.com/91123594/138903802-926799f2-4e76-4f63-8e57-84e48e723bab.png)


