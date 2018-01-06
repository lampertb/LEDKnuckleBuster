
[gif]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/touchExample.gif "LED Knuckle Buster In Action"
[datasheet]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/datasheet.png "Darlington NPN Datasheet"
[dxfExample]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/dxfExample.png "Exporting DXF Design"
[equation1]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/equation1.png "Base current equation"
[equation2]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/equation2.png "Base current equation"
[equation3]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/equation3.png "Base current equation"

[handFist]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/handFist.jpg "LED Knuckle Buster In Action"
[layout]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/layout.png "Board layout with fill"
[productPhoto]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/productPhoto.jpg "LED Knuckle Buster In Action"
[schematic]: https://github.com/lampertb/LEDKnuckleBuster/blob/master/Images/schematic.png "LED Knuckle Buster Schematic"

![alt text][gif]

# LED Knuckle Busters, light up your fists!
## By Ben Lampert

Designed and manufactured by Ben Lampert at Chicago's mHub maker space (https://mhubchicago.com/) these LED's brass knuckles are a fun toy to play with. Conductive finger holes turn on high gain transistors that lights up LED's based on the strength of the grip; just put your fingers through the hole and squeeze!

* Features:
  * Brass knuckle finger spacing fits most adults and children.
  * 100% Analog circuitry features low power operation when not in use.
  * Touch sensitive design, just make a fist to turn on the LED's!

* Requires:
  * Blue LED Brass Knuckle board (.brd files available)
  * Parts http://www.digikey.com/short/q8q7pt

* Specs
  * Height: Approx 115mm
  * Width: Approx 50mm
  * Powered by two coin cell batteries


## Project Details:

The LED Knuckle Buster mechanical and board outline was originally inspired by this thingiverse brass knuckle.
https://www.thingiverse.com/thing:1160010

I decided to make an LED version, and after downloading used solidworks to create and exporting a DXF of the outer perimeter of the model. This DXF was then important as layer 20 (board outline) in eagle to create the PCB board outline.

![alt text][dxfExample]

The circuit I think it pretty clever. I originally thought to use a microcontroller and a technique similar to the mAkey mAkey (https://makeymakey.com/). However, it seems like I put MCU’s on everything these days, so I revisited a 100% analog design.

What I came up with I think it simple and clever. The copper on the backside of the board is a VCC plan, as the fingers extend through the holes that make contact with the base of a darlignton pair. Given you skin resistivity is ~100k (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2763825/) you get a small amount of current running through your fingers.

Just as a ballpark, that current using a Darlington Pair is approximately:

![alt text][equation1]

![alt text][equation2]

![alt text][equation3]


Reviewing the cheapest Darlington Pair NPN available on Digikey
https://www.diodes.com/assets/Datasheets/ds30047.pdf

![alt text][datasheet]

This has a gain of 5,000-10,000. So our 46uA base current becomes 23-46mA of current. Not bad for small leakage through your finger!

That current is plenty to turn on a LED, so with that in mind this is the final circuit I designed.

![alt text][schematic]
![alt text][layout]

Rev A:
Forgot to connect the via for VCC to connect to the other side of the board, whoop!
Also, forgot a pull down on the base which caused FING4 LED to always be on.

Rev B:
Everything is tested ok! Time to Ship It!

![alt text][productPhoto]

![alt text][handFist]



