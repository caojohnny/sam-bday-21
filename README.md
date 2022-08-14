# `sam-bday-21`

PCB I designed as a gift for my roommate's 21st birthday.

It's an LED flasher using an astable 555 chip and powered off an AA battery.
The aesthetic design is two antennas on the silkscreen since he's interested
in RF.

# Problems

I stayed up late on the design so there is a number of major design problems
with the board, the main ones documented on the schematic which can be found
in the `preview/` folder.

On the schematic side, I forgot to change the 10u cap on the 555 to 15u and
ended up ordering the wrong value, so the LEDs alternate at around 600 ms as
opposed to the full 1 second I was hoping that it would. The second major error
was the resistors were not sized correctly because I misinterpreted the I-V
curves on the LED datasheets; they should have been double the size. This
results in around 500 mA current draw which I did not design the layout to
handle.

On the layout, the transistor footprint was completely wrong, I read the
datasheet as having a SOT-89 as opposed to the "SC-89" which is a SOT-416. 
This was bodged onto the PCB by rotating the transistor and using a wire to
connect the gate around the footprint. The main goal on the front side was to
avoid as much copper as possible for aesthetic reasons, but this lead to me
not utilizing a 5V plane on the front, which ended up being just unclean and
reduces the thermal dissipation for the LEDs. The backside was not designed
very cleanly and the trace widths are not properly sized in a number of
locations. Finally, there is awful noise on the output of the 555 which I
haven't investigated, but it appears not to affect function.

Overall, the board behaves correctly at the wrong frequency, but it still does
relatively close to what I designed it to do.

# Software

[KiCad](https://www.kicad.org/)

