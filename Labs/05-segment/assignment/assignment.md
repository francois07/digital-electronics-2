# Lab 5: François Soulié

Link to your `Digital-electronics-2` GitHub repository:

[https://github.com/francois07/digital-electronics-2](https://github.com/francois07/digital-electronics-2)

### 7-segment library

1. In your words, describe the difference between Common Cathode and Common Anode 7-segment display.

   - CC SSD : Active high
   - CA SSD : Active low

2. Code listing with syntax highlighting of two interrupt service routines (`TIMER1_OVF_vect`, `TIMER0_OVF_vect`) from counter application with at least two digits, ie. values from 00 to 59:

```c
/**********************************************************************
 * Function: Timer/Counter1 overflow interrupt
 * Purpose:  Increment counter value from 00 to 59.
 **********************************************************************/
volatile uint8_t cnt0 = 0;
volatile uint8_t cnt1 = 0;

ISR(TIMER1_OVF_vect)
{
    if(cnt0 > 9){
        cnt0 = 0;
        cnt1++;
    }
    if(cnt1 > 5){
        cnt1 = 0;
    }
    cnt0++;
}

/**********************************************************************
 * Function: Timer/Counter0 overflow interrupt
 * Purpose:  Display tens and units of a counter at SSD.
 **********************************************************************/
ISR(TIMER0_OVF_vect)
{
    static uint8_t pos = 0;
    if(pos > 1) pos = 0;
    switch(pos){
        case 0:
            SEG_update_shift_regs(cnt0, pos);
            break;
        case 1:
            SEG_update_shift_regs(cnt1, pos);
            break;
    }
    pos++;
}
```

1. Flowchart figure for function `SEG_clk_2us()` which generates one clock period on `SEG_CLK` pin with a duration of 2us. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

   ![flowchart](./CLK_flowchart.png)

### Kitchen alarm

Consider a kitchen alarm with a 7-segment display, one LED and three push buttons: start, +1 minute, -1 minute. Use the +1/-1 minute buttons to increment/decrement the timer value. After pressing the Start button, the countdown starts. The countdown value is shown on the display in the form of mm.ss (minutes.seconds). At the end of the countdown, the LED will start blinking.

1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.

   ![kitchen alarm](./kitchen_alarm.png)
