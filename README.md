# DEFCON 32 Free Wili Free LED Bracelet
The company Free Wili was providing LED bracelets with custom printing on them advertising their new flipper-but-better device Free Wili. Here are notes from taking it apart. Initially the goal was take it apart because I could not believe it would just be an LED bracelet and that's it. Once I saw the radio receiver, I then wanted to figure out what sort of signals could control this bracelet.

## Pics
<img width="652" alt="image" src="https://github.com/user-attachments/assets/a37c8d57-b030-47b4-9855-40d83739c893">
<img width="877" alt="image" src="https://github.com/user-attachments/assets/4d1ff1c3-cf65-4be7-b0d1-1a500d160e9f">
<img width="652" alt="image" src="https://github.com/user-attachments/assets/6102e656-424e-4c9e-9d25-75de78078633">

## Components
- CMT2220LS
  - OOK Receiver that mostly works at 433.92 Mhz
  - https://crossic.com/wp-content/uploads/2022/02/CMT2220LS-Datasheet-EN-V1.0-20210917.pdf
- Markings-scrubbed SOP 8 IC
  - Clearly the brains of the operation though, given central location
- 13.52127 MHz crystal
- 2x CR2032 battery
- 2 Multi-color LEDs
- A button
 
## Notes
The PCB has the text:
`HE-B158ST1K1` 
on it. When you search that, it'll show a few sites for Xyloband that is used at some concerts and events, as well as some of the shopping sites that re-sell this. Nothing too useful for this though.

The battery is interesting because the positive side is connected to the board through a coil/spring wrapped around a mounting hole.

There is no "off-state". If the batteries are connected, the device is powered. When the LEDs aren't running, the device is still on, running at 5-5.5v. 

The DOUT of the radio IC connects to pin 3 of the unmarked IC.

### Unmarked IC

Best I can tell, this is what the pins are.

<img width="1244" alt="image" src="https://github.com/user-attachments/assets/3cac5526-5bb6-4486-b6b4-22bee2f29a32">

Could not determine what the chip was. Interfacing with it is likely done on pins 2 or 3 though.

### Pin 2 and 3
Pin 2 goes low occaisonally and shortly after Pin 3 has a bunch of signals.
<img width="1102" alt="image" src="https://github.com/user-attachments/assets/c3d7e53c-826a-40e2-8f0c-55cbd8c32d29">

The Pin 2 stays low for ~162.400 ms (+/- 0.005) and then bounces back up. In one instance, it went low for 162.400 ms, then went high. Pin 3 stays mostly low but goes high every 40-50 us. Then 26.602 ms later, Pin 2 goes low for 132.130 ms.

## Controlling Radio Signals
Free Wili posted the Flipper format .sub files to control the LEDs [in this repo](https://github.com/freewili/bracelet_subfiles).

I'm reasonably certain these were given away so that people who bought the Free Wili board or the Whale Tail had some things to mess with: namely people wearing the LED bracelets. Pretty clever!
