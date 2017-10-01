# Uniboard

-> tentative schematics [here](/include/UniBoard/UB-v0.pdf)

## Overall remarks

* Form factor: Raspberry Pi Hat (with screws places for both Raspberry Pi 3 and Raspberry Pi 0)
* Have the __Oled__, __ADC__, __TGC__, __HV__, __Pulser__, __capa touch__ parts clearly separated (rectangle silkcreen + names)
* ADCs: both a 12 bit ADC and the only SPI ADC
* Layers: 4 layers, if possible to have the RF noise as low as possible
* Components: easily sourcable in MacroFab

## OLED 

* Maintaining room for the the 0.96" variant on the top of the board

## ADC
 
* Jumper to select SPI ADC (goblin) or 12 bit 10Msps ADC (onboard - that can work at 10Msps )
  * Only 10 MSPS 12bit ADC. The faster ADC, like AD9629 costs approximately the same, but more complicated in use (SPI configuration, diff clock, 1.8V supply etc)
* If 10Msps ADC:
    * Jumper to select _Raw Signal_ or _Enveloppe_ . If RawSignal, to be offset by Vref/2.
* If SPI ADC:
    * Only _Enveloppe_
    * no need for variable Vref... as gain can be controlled beforehand.
* Jumper to select signal input to RPin .. or not.
* Ideally, the two ADCs can be shut down, and signal routed to RPin - in case I want to use the interleaved ADCs.

## TGC (ex goblin board)

* MD0100 or equivalent for protection of VGC
* Jumper : to select gain from pot (as per goblin) or from external (0 to 1V - connected to the 6x2 header Gain) as per goblin
* Transfo: replace with one easily sourced from digikey / macrofab :)

## HV (ex tobo board)

* Jumper: Selectable 0, 25, 50 or 75V

## Pulser (ex tobo board)

* Unipolar, only with Pon and Poff (routed to 2x20 Raspberry header)
* Jumper: route pulse either to SMA or to "artificial" piezo   (see RLC) that can stand the pulses.
  * RLC : see for example http://www.brl.uiuc.edu/Downloads/bigelow/APPENDIX%20C.PDF

## Other

* One 6x2 header for add-ons (Pon, Poff, 5V, 3.3V, Gain, Touch Interrupt, TGC, GND, SDA, SCL, PWM, Tracker). Silkscreen for the different items
* Leds on the 3.3V line and 5V line


## Capa touch

* I'd like to have 2 or 3 touch pad like zones, to be connected to i2c bus + 1 interrupt pin for detection of touching this zones.

# Overview

![](/include/images/UniPins.png)


# Pins

![](/include/images/UniDesign.jpg)


# Back and forth

