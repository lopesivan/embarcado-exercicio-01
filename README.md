Makefile based on [balau82](https://balau82.wordpress.com/about-me) article, posted on 03/13/2011

# Blink

## Programming Arduino Uno in pure C


The Port "B" of the microcontroller can be changed bit by bit with special
instructions called "sbi" and "cbi". In C we use the bitwise "|=" and "&="
assignment operators, which usually read and write a variable, but the
compiler recognizes those kind of accesses generating optimized assembly in
case of bit-wise operations, and there is no read operation involved. The
"_BV" macro together with PORTB5 is used to build a value that contains one on
the bit that corresponds to PB5. The main function contains an infinite loop
that raises and lowers the bit 5 of PORTB register and between these
operations waits for one second using the library function "_delay_ms". If you
installed avr-gcc on your Linux machine, the ports definitions and useful
macros (like "_BV") can be found in the "/usr/lib/avr/include/avr/iom328p.h"
and "/usr/lib/avr/include/avr/sfr_defs.h" headers, or in the directory where
the library has been installed.

The compiler is able to create an ELF executable program that contain machine
code and other information such as program section memory layout and debug
information. In order to compile a program and upload it to the Arduino Uno,
We need to create an IHEX file and use the avrdude tool to load it inside the
Flash. The tool to convert the ELF into IHEX in our case is avr-objcopy. Now
it's time to run the command lines that build and upload the LED blink
program. Most of the parameters and options of the avr-gcc and the avrdude
tools for the Uno board can be found in the "hardware/arduino/boards.txt" file
from inside the Arduino IDE installation directory, and some other information
is present in the avrdude manual.


Credits:
https://balau82.wordpress.com/2011/03/29/programming-arduino-uno-in-pure-c
