# Set up method
1) cli(); //Disable all interrupts
2) TCCR2A = 0 //Good practise to disable all registers before setup
3) TCCR2B = 0 //Good practise to disable all registers before setup
4) TCNT0 = 0 //Counter value
5) OCR2A = 254; (Max value = V - 1)
6) TIMSK2 = 1 << 2 //Enable timer 2 interrupts
7) sei(); //Enable all interrupts

### ISR
```
ISR(TIMER1_COMPA_vect)
  {
  (ISR FUNCTION)
  }
```
TIMER(1) = timer 1 or 0
COMP(A) = timer A or B
vect (just follow)

## Timers on the Atmega328
1) Timer 0 and 2 (8 bit timers) can count from 0 to 255
2) Timer 1 (16 bit timer) can count from 0 to 65535

## Using timers to generate a waveform

![](Timers%20Lecture.pdf#page=6&rect=39,95,570,465&color=yellow|Timers%20Lecture,%20p.6)
TCNT0 = Count value (set to 0 at the start)
OCR0A = Max value before it sends an interrupt

## Prescaler formula


![](Timers%20Lecture.pdf#page=7&rect=59,188,638,384&color=yellow|Timers%20Lecture,%20p.7)

P = prescalar value (1,8,64,256...)
Fclk = depends on the chip on the Arduino Uno
res = resolution

"The prescalar is chosen using bits 2 to 0(CS02:00) of TCCR0B" [](Timers%20Lecture.pdf#page=8&selection=11,0,11,60&color=yellow|Timers%20Lecture,%20p.8)
Choose the correct bits based on the table and set it to the corresponding resgisters
![](Timers%20Lecture.pdf#page=8&rect=148,118,591,312&color=yellow|Timers%20Lecture,%20p.8)

## Interrupt mode
"The TIMER0_COMPA (TIMER0_COMPA_vect) interrupt is triggered whenever TCNT0 reaches the 
top timer value V and rolls back to 0" [](Timers%20Lecture.pdf#page=9&selection=12,0,18,19&color=yellow|Timers%20Lecture,%20p.9)

![](Timers%20Lecture.pdf#page=9&rect=49,199,674,295&color=yellow|Timers%20Lecture,%20p.9)
res = resolution
V/OCR0A = max value
T<sub>cycle</sub> = the time which the timer triggers the timer interrupt
![](Timers%20Lecture.pdf#page=13&rect=111,109,576,381&color=yellow|Timers%20Lecture,%20p.13)

## Setup of TCCR0A

![](Timers%20Lecture.pdf#page=14&rect=112,279,578,349&color=yellow|Timers%20Lecture,%20p.14)

bits (7 and 6) is used to control what to do with OC0A each time we hit the top value ![](Timers%20Lecture.pdf#page=14&rect=182,122,572,222&color=yellow|Timers%20Lecture,%20p.14) 
normal = off
toggle = 1 -> 0 -> 1
clear = 0 when top value is hit
set = 1 when top value is hit

![](Timers%20Lecture.pdf#page=15&rect=39,157,654,388&color=yellow|Timers%20Lecture,%20p.15)
WGM00:03 control the waveform generation mode of the triangle signal (unit step)
CTC mode = clear timer on compare match

TCCR0A is connected to the TCCR0B (might have registers that are there)
refer to datasheet

![](Timers%20Lecture.pdf#page=17&rect=127,214,574,290&color=yellow|Timers%20Lecture,%20p.17)
FOC0A:B is not used
WGM02 is waveform generation mode 
CS00:02 controls the prescalar value (choose the value that is closest to 255 | theoretical limit)![](Timers%20Lecture.pdf#page=8&rect=145,118,584,312&color=yellow|Timers%20Lecture,%20p.8)
"Note: Setting CS02:CS00 bits to anything other than 000 automatically begins the timer" [](Timers%20Lecture.pdf#page=17&selection=36,0,39,9&color=yellow|Timers%20Lecture,%20p.17)

"We must also enable global interrupts using the sei(); function call" [](Timers%20Lecture.pdf#page=17&selection=42,0,45,17&color=yellow|Timers%20Lecture,%20p.17)



