# Intergalactic Module Format - v1.0
The Intergalactic Module Format is a set of standard communication protocols for microcontroller-based music hardware. It features both analog and digital signals and analog audio. A collection of Intergalactic modules in a case is known as a deck.

## Physical Dimensions
Modules are 128.5mm high and have a width which is a multiple of 5.08mm, compatible with Eurorack module sizes. 3.5mm jacks are used for audio connections. 

## Power
Power connectors use a JST PH 2-pin connector with a black ground wire and a red power wire. The module should be able to accept power from 3.3V to 5V with a maximum power draw of 500mA.

## Audio
Audio signals are analog. Output jacks are at line out level +2V to -2V and an impedence between 100 Ω and 600 Ω. Input jacks are at line in level of +2V to -2V and an impedence of 10 kΩ.

Special jacks can also be included in a module for headphone output, microphone or instrument input, and connecting to speakers. As these alternatives jacks are not module-to-module connections, they are not fully detailed in the specification and should follow established audio engineering best practices.

## Control
There are two basic categories of control signals: I2C and GPIO. I2C control signals are digital and use the I2C protocol. Intergalactic I2C uses 3.3V system voltage in 100 kbit/s standard mode without the need for clock stretching. Modules must allow for address reprogramming so that multiple modules of the same type can be used in one system.

I2C control lines use a Qwiic connector. This is a 4-pin JST 1mm connector. The pinout is GND, 3.3V, SDA, SCL. The wire colors are black for GND, red for 3.3V, blue for SDA, and yellow for SCL.

A module can either have one Qwiic port or two. It is preferred that they have two in order to allow for daisy chaining of modules. When two port are available, either one can be used, or both can be used in the case of daisy chaining. There are some rare special cases where a module may have more than two Qwiic ports or where the Qwiic ports are not interchangeable, but this will not be the case for the majority of modules.

The other type of control signal is GPIO. GPIO signals can be either analog or digital. The signals range from 0 to 3.3V and are just standard microcontroller GPIO pins and therefore can carry many different types of signals such as binary digital signals, PWM, and analog voltage.

### Control Commands
Intergalactic control commands cover all of the common types of control signals used in a modular system for the expression of musical ideas. Examples include pitch, tempo, turning individual notes on and off, controlling expression parameters such as tremelo, and general purpose control signals such as gates.

### Routing
In modular systems which use analog control signals, routing of control signals is done the same way as routing of audio signals, through patching between jacks using patch cables. This is not the case with Intergalactic control signals. All of the control signals are on the same bus. Connecting them together adds them to a common network. Audio routing is handled by patch cables in a similar manner to other modular systems and the audio world in general.

### Command Reference
- [[Clock Signals]]
- [[Tuning Signals]]

### GPIO Signals
- [[Gate Signals]]

## Modules
The are an unlimited number of possible modules. Common module types are discussed here.

- [[Clock source]]
- [[Oscillator]]
- [[Envelope]]
- [[Filter]]
- [[Amplifier]]
- [[Audio Input]]
- [[Audio Output]]