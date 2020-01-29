# C64_Font8x8

8x8 C64 font for OLED libraries with some additional custom characters (128 to 143) that I found useful, but perhaps you notsomuch. :-)

This repository contains header files for the following libraries:
- [Tiny4kOLED](https://github.com/datacute/Tiny4kOLED)
- [ACROBOTIC_SSD1306](https://github.com/vivchawda/arduino/tree/master/libraries/ACROBOTIC_SSD1306)

I am sure that the files can be easily adapted to the OLED library that you are using. If you succeeded, drop me a line so I can add it to this repository.

## Usage

### Tiny4kOLED
1) Copy the relevant header file into your Arduino project directory.

2) Call `setFont()` with the new available definition, like so:
```
#include <Tiny4kOLED.h>
#include "font8x8_c64.h"        /* includes the font definition */

void setup()
{
    oled.begin();
    oled.setFont(FONT8X8_C64);  /* apply the font definition */
}
```
Re-compile your sketch and you should see the new font!


### ACROBOTIC_SSD1306 
(This is what I originally created the font for a few years ago. I am not so sure this library is still maintained.)

Using it with this library is not so straightforward as with the Tiny4kOLED one. 

1) The relevant header file needs to be copied inside the ACROBOTIC_SSD1306/fonts/ directory.

2) Then, the ACROBOTIC_SSD1306.h file needs to be patched to include this header file:
```
Line 49:	#include "fonts/font8x8.h"
Line 50:	#include "fonts/font8x8_c64.h" /* add this line */
Line 51:	#include "fonts/font5x7.h"
```

3) In ACROBOTIC_SSD1306.cpp, the following line needs to be replaced, as it initialises with a 5x7 font by default:

```
Line: 199:	setFont(font5x7); /* replace this line */
Line: 199:	setFont(font8x8_c64);
```

Re-compile your sketch and you should see the new font.

