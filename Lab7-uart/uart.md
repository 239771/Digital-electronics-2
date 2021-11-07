# Lab 7: Jesús Borobia

Link to this file in your GitHub repository:

[https://github.com/239771/Digital-electronics-2](https://github.com/239771/Digital-electronics-2)

### Analog-to-Digital Conversion

1. Complete table with voltage divider, calculated, and measured ADC values for all five push buttons.

   | **Push button** | **PC0[A0] voltage** | **ADC value (calculated)** | **ADC value (measured)** |
   | :-: | :-: | :-: | :-: |
   | Right  | 0&nbsp;V | 0   | 0 |
   | Up     | 0.495&nbsp;V | 101 | 99 |
   | Down   |  1.203   V  | 246    | 256 |
   | Left   |   1.969 V    | 403    | 410 |
   | Select |   3.182 V    |  651   | 640 |
   | none   |   5 V    |  1023   | 1023 |

2. Code listing of ACD interrupt service routine for sending data to the LCD/UART and identification of the pressed button. Always use syntax highlighting and meaningful comments:

```c
/**********************************************************************
 * Function: ADC complete interrupt
 * Purpose:  Display value on LCD and send it to UART.
 **********************************************************************/
ISR(ADC_vect)
{
    uint16_t value = 0;
    char lcd_string[4] = "0000";

    value = ADC;                  // Copy ADC result to 16-bit variable
    itoa(value, lcd_string, 10);  // Convert decimal value to string

    lcd_gotoxy(8,0);	//Clear position
	lcd_puts("   ");
	lcd_gotoxy(8,0);	//Display dec
	lcd_puts(lcd_string);
	
	itoa(value,lcd_string,16);	//Dec to hex
	lcd_gotoxy(13,0);//Clear previous and show hexa
	lcd_puts("   ");
	lcd_gotoxy(13,0);
	lcd_puts(lcd_string);
	
	lcd_gotoxy(8,1); //Clear prev.
	lcd_puts("   ");
	lcd_gotoxy(8,1);
	
	 if (value>=50)         //Search for the range of value
	 {
		if (value>150)
		{
		 if (value>300)
	     {
		  if (value>500)
		  {
	       if (value>800)
		   {
			 lcd_puts("none"); uart_puts("none");    //We can see pressed button in LCD and in the PC  
		   }
		   else lcd_puts("Select"); uart_puts("Select"); 
		   }
				 else lcd_puts("Left"); uart_puts("Left"); 
			 }
			 else lcd_puts("Down"); uart_puts("Down"); 
		 }
		 else lcd_puts("Up"); uart_puts("Up"); 
	 }
	 else lcd_puts("Right"); uart_puts("Right"); 
	 
	 uart_puts(" ");
	 uart_puts(lcd_string); //Show hexa 
}
```

### UART communication

1. (Hand-drawn) picture of UART signal when transmitting three character data `De2` in 4800 7O2 mode (7 data bits, odd parity, 2 stop bits, 4800&nbsp;Bd).

   ![your figure]()

2. Flowchart figure for function `uint8_t get_parity(uint8_t data, uint8_t type)` which calculates a parity bit of input 8-bit `data` according to parameter `type`. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

   ![your figure]()

### Temperature meter

Consider an application for temperature measurement and display. Use temperature sensor [TC1046](http://ww1.microchip.com/downloads/en/DeviceDoc/21496C.pdf), LCD, one LED and a push button. After pressing the button, the temperature is measured, its value is displayed on the LCD and data is sent to the UART. When the temperature is too high, the LED will start blinking.

1. Scheme of temperature meter. The image can be drawn on a computer or by hand. Always name all components and their values.

   ![your figure]()
