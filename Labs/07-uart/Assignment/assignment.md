# Lab 7: François Soulié

Link to this file in your GitHub repository:

[https://github.com/francois07/digital-electronics-2](https://github.com/francois07/digital-electronics-2)

### Analog-to-Digital Conversion

1. Complete table with voltage divider, calculated, and measured ADC values for all five push buttons.

   | **Push button** | **PC0[A0] voltage** | **ADC value (calculated)** | **ADC value (measured)** |
   | :-------------: | :-----------------: | :------------------------: | :----------------------: |
   |      Right      |         0V          |             0              |            0             |
   |       Up        |        0.5V         |            101             |            99            |
   |      Down       |        1.2V         |            245             |           257            |
   |      Left       |        1.97V        |            402             |           409            |
   |     Select      |        2.6V         |            650             |           639            |
   |      none       |         5V          |            1022            |           1023           |

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

    lcd_gotoxy(8, 0);
	lcd_puts("    ");
	lcd_gotoxy(8, 0);
	lcd_puts(lcd_string);

	lcd_gotoxy(8, 1);
    lcd_puts("    ");
	lcd_gotoxy(8, 1);

    if(value < 1024 && value > 1022) lcd_puts("right");
    else if(value < 110 && value > 91) lcd_puts("up");
    else if(value < 260 && value > 230) lcd_puts("down");
    else if(value < 415 && value > 489) lcd_puts("left");
    else if(value < 670 && value > 630) lcd_puts("select");
}
```

### UART communication

1. (Hand-drawn) picture of UART signal when transmitting three character data `De2` in 4800 7O2 mode (7 data bits, odd parity, 2 stop bits, 4800Bd).

   ![wavedrom](./wavedrom.png)

2. Flowchart figure for function `uint8_t get_parity(uint8_t data, uint8_t type)` which calculates a parity bit of input 8-bit `data` according to parameter `type`. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

   ![flowchart](./flowchart.png)

### Temperature meter

Consider an application for temperature measurement and display. Use temperature sensor [TC1046](http://ww1.microchip.com/downloads/en/DeviceDoc/21496C.pdf), LCD, one LED and a push button. After pressing the button, the temperature is measured, its value is displayed on the LCD and data is sent to the UART. When the temperature is too high, the LED will start blinking.

1. Scheme of temperature meter. The image can be drawn on a computer or by hand. Always name all components and their values.

   ![temp schema](./temp_schema.png)
