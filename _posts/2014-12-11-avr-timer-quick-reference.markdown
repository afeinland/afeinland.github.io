---
layout: post
title: "AVR Timer Quick Reference"
date: 2014-12-10 19:11:13
categories: blog post
---

This guide is written for myself and anyone else who has used timers on an AVR in the past but could use a quick refresher. If you would like a more in depth explanation, I recommend these tutorials: [EngBlaze](http://www.engblaze.com/microcontroller-tutorial-avr-and-arduino-timer-interrupts/ "EngBlaze") and [AVRFreaks](http://www.avrfreaks.net/forum/tut-c-newbies-guide-avr-timers "AVRFreaks")

===

The code below is written for the ATMega328, but should be relevant to most modern AVR chips.

{% highlight c %}
/* This function configures Timer/Counter 1 on the ATMega328 to call an ISR every 500ms.
 * Specifically, we are configuring the timer for Mode 4, which increments from 0
 * up to TOP (OCR1A, in this case), get set back to 0, and starts the whole process over again.
 * When the value in TCNT1 equals the value in OCR1A, the Timer/Counter1 Compare Match A interrupt is triggered.
 *
 * NOTE: We are assuming that the chip (specifically fCLK_IO) is running at 8mhz.
 */
void timer_init(void)
{
    /* Enable global interrupts. This allows the ISR to be called.
     *
     * NOTE: "SREG |= 0x80;" will also work. 
     */
    sei();

    /* OCR1A holds the TOP value for TCNT1 in Mode 4. This is the value that determines the resolution of the timer.
     * 1250 is the number of times the timer will increment in 100ms (our desired period),
     * with a CPU frequency of 8mhz and prescaler of 64. The value for OCR1A can be calculated with the equation:
     * (fCLK_IO * desired_period) / prescale_value. In our case, the equation would be 8000000 * 0.5 / 64 = 62500.
     */
    OCR1A = 62500;

    /* The Output Compare Interrupt Enable 1A flag enables the Compare Match A interrupt for Timer/Counter 1.
     * This flag must be set to enable the TIMER1_COMPA_vect ISR.
     */
    TIMSK1 = (1 << OCIE1A);

    /* The CS11 and CS10 (Clock Select) bits set the prescale value to 64. Setting these bits starts the timer.
     * (With a prescale value of 64, TCNT1 will increment every 64 clock cycles, or,
     * with a CPU frequency of 8mhz, 125000 times per second.)
     * 
     * The WGM12 (Waveform Generation Mode)bits sets the timer to Mode 4.
     * See the function comment above or the ATMega328's data sheet for more info.
     */
    TCCR1B = (1 << WGM12) | (1 << CS11) | (1 << CS10);
}
{% endhighlight %}

===

View the whole program [on Github](https://github.com/afeinland/AVR_Timer_Tutorial "code on Github").

