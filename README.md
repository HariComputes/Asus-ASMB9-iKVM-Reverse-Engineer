# Asus-ASMB9-iKVM-Reverse-Engineer
These pricey little things. for just a ROM chip on a PCB. This is a breakdown on what connects where and through what.

Since doing this fact finding excersize. seems someone had already done the heavy lifting here:
https://forums.servethehome.com/index.php?threads/asus-p11c-i-with-asmb9-ikvm-after-fw-update-password-not-working.31905/page-2#post-315667

## Chip

The ROM used here is a MXIC MX25L25735FMI-10G

## Board Pictures (Without Stickers)

<img width="504" height="328" alt="IMG-20260703-WA0008" src="https://github.com/user-attachments/assets/3fda54ef-0671-451b-b21b-3d629550dedc" />
<img width="504" height="328" alt="IMG-20260703-WA0014r" src="https://github.com/user-attachments/assets/4c40d229-579b-4f3f-aa6f-a2e197dc7218" />

The stickers just have production/manufacturer tracking numbers, as well as a couple of serial numbers and which hardware revision code the PCB is. This one is revision B4.

## Pinouts and Diagrams

The pins are from the J1 connector to the MXIC chip.
Pin 3 is used as a keying pin (Blank/Blocked)

This is the diagram I used for the J1 connector:

<img width="116" height="177" alt="j1" src="https://github.com/user-attachments/assets/1816e7e2-80f8-414c-aaac-2fd12aaeca79" />
<br>
<br>
This is the pinout for the MXIC chip:
<br>
<img width="261" height="163" alt="image" src="https://github.com/user-attachments/assets/f39ed310-4fc5-45f7-a926-e26aeb5ebbd2" />
<br>
turns out the manual has the pinouts in it 🤦‍♂️
<img width="1093" height="629" alt="image" src="https://github.com/user-attachments/assets/80a3ed2e-4475-4514-96ef-09d948eac00f" />

## Pin Traces

The format is as follows:<br>
J1 Connector Pin|intermediary (Resistors or Diodes)|ROM PIN
--- | --- | --- |
1 | N/A | 15 (SI)
2 | N/A | 2 (VCC)
3 (Keying Pin) | N/A | N/A
4 | N/A | 7 (Chip Select)
5 | N/A | NC
6 | 15ohm | 8 (SO)
7 | JP1/R7 (Not Populated) | NC
8 | N/A | 16 (SCLK)
9 | N/A | 10 (GND)
10 | resister/jumper under q1 | NC
11 | diode 0.5v | 10 (GND)
12 | N/A | NC
13 | R4 (blank resistor loc. Silkscreen misprint) | 10 (GND)
14 | N/A | NC

Other info
Between ROM Pin 2 (VCC) to ROM Pin 11 (GND) is a diode 0.5v. (Could be related to the LED circuit below?)

On the back of the board. Side without the ROM on it
J1 Pin 2 (VCC) to resistor 217ohm (0.217k) to Positive anode of led
J1 Pin 11 (GND) - negative anode of led


