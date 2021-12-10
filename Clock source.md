# Clock Source

A clock source generates clock signals. A clock signal represents a global tempo which can be used by several different types of modules such as sequencers and drum machines.

Intergalactic modules use a digital clock signal sent as an I2C command. The clock source either periodically sends out clock signal commands or can be periodically polled.

The clock signal conveys the following information:
- the tempo in stella units
- the phase, in other words the difference in time between now and when the last beat happened in milliseconds
- (optional) the absolute time in milliseconds since the epoch

## Where does the clock source get its time and tempo information?
The tempo is a matter of preference, so it can be input from the user via a user element interface such as a knob or it can be algorithmically generated. It can also come from another source such as a MIDI converter.

The phase is in relative time, so the microcontroller only needs to know when the last beat happened. Many microcontrollers have a way to keep track of the time elapsed since they were powered on. For instance, on Arduino microcontrollers the milis() command can be used.

The optional absolute time requires that the microcontroller have a real-time clock (RTC) that has been set accurately or another time source. One excellent time source is a GPS receiver. Computers also often have an accurate time and time information can be obtained from the Internet when Internet access is available. Timezones are not used for the absolute time. When the correct time is not known, it is best to omit this optional parameter. However, when it is available, it allows some useful synchronization between decks.