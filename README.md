OBD9141
=======

This is a library to read data from the [OBD-II][obd2] port through the K-line pin using either ISO 9141-2 or ISO 14230-2 (KWP).

There are numerous projects which read data from the diagnostic port and display or record this. However, I found that most of these projects either use an ELM327 chip or the communication code is interwoven with the rest of the program. This makes it hard to extract the communication parts for use in another project.

The goal of the library is to provide a simple class which handles the communication with the port. Additionally a second class has been created which can simulate responses for testing purposes.

00 ! PIDs supported [01 - 20]
01 ! Monitor status since DTCs cleared|{0[0]:s}\n{0[1]:s}\n{0[2]:s}\n{0[3]:s}\n{0[4]:s}\n{0[5]:s}\n{0[6]:s}\n{0[7]:s}\n{0[8]:s}\n{0[9]:s}\n{0[10]:s}\n{0[11]:s}
02 ! Freeze DTC - {0:s}
03 Fuel system status|\n{0[0]:s}: {0[1]:s}\n{0[2]:s}: {0[3]:s}
04 Calculated engine load|{0:3.2f}%|0|100|90
05 Engine coolant temperature|{0:3.0f}°C|-40|215|100
06 Short term fuel trim—Bank 1|{0:3.2f}%|0|100|50
07 Long term fuel trim—Bank 1|{0:3.2f}%|0|100|50
08 Short term fuel trim—Bank 2|{0:3.2f}%|0|100|50
09 Long term fuel trim—Bank 2|{0:3.2f}%|0|100|50
0A % Fuel pressure (gauge pressure)|{0:5.0f} KPa|0|765|450
0B Intake manifold absolute pressure|{0:5.0f} KPa|0|255|150
0C Engine RPM|{0:5.0f} RPM|0|16383|6500
0D Vehicle speed|{0:3.0f} Km/h|0|255|113
0E Timing advance|{0:3.2f}° BTDC|-64|63.5|25
0F Intake air temperature|{0:3.0f}°C|-40|215|100
10 MAF air flow rate|{0:5.0f} g/s|0|655|500
11 Throttle position|{0:3.2f}%|0|100|90
12 Commanded secondary air status|{0:s}
13 Oxygen sensors present|{0[0]:s}: {0[1]:08b} - {0[2]:s}: {0[3]:08b}
14 Oxygen Sensor 1|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
15 Oxygen Sensor 2|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
16 Oxygen Sensor 3|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
17 Oxygen Sensor 4|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
18 Oxygen Sensor 5|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
19 Oxygen Sensor 6|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
1A Oxygen Sensor 7|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
1B Oxygen Sensor 8|{0[0]:3.2f}V|0|1.275|0.64|{0[1]:3.2f}%|0|100|50
1C OBD standards this vehicle conforms to|{0:s}
1D Oxygen sensors present (in 4 banks)|{0:s}
1E Auxiliary input status|{0:s}
1F Run time since engine start|{0:5.0f}
20 ! PIDs supported [21 - 40]
21 Distance traveled with MIL on|{0:5.0f} Km
22 Fuel Rail Pressure (relative to manifold vacuum)|{0:5.0f} KPa|0|5177|3000
23 Fuel Rail Gauge Pressure (diesel, or gasoline direct injection)|{0:5.0f} KPa|0|655350|400000
24 Oxygen Sensor 1 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
25 Oxygen Sensor 2 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
26 Oxygen Sensor 3 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
27 Oxygen Sensor 4 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
28 Oxygen Sensor 5 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
29 Oxygen Sensor 6 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
2A Oxygen Sensor 7 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
2B Oxygen Sensor 8 AB: Fuel–Air Equivalence Ratio CD: Voltage|{0[0]:3.2f}V|0|2|1.5|{0[1]:3.2f}%|0|8|6
2C Commanded EGR|{0:3.2f}%|0|100|90
2D EGR Error|{0:3.0f}%|-100|100|50
2E Commanded evaporative purge|{0:3.0f}%|0|100|90
2F Fuel Tank Level Input|{0:3.0f}%|0|100|90
30 Warm-ups since codes cleared|{0:3.0f}
31 Distance traveled since codes cleared|{0:3.0f} km|0|65535
32 Evap. System Vapor Pressure|{0:3.2f} pa|-8192|8191.75|5000
33 Absolute Barometric Pressure|{0:5.0f} KPa|0|255|150
34 Oxygen Sensor 1 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
35 Oxygen Sensor 2 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
36 Oxygen Sensor 3 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
37 Oxygen Sensor 4 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
38 Oxygen Sensor 5 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
39 Oxygen Sensor 6 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
3A Oxygen Sensor 7 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
3B Oxygen Sensor 8 AB: Fuel–Air Equivalence Ratio CD: Current|{0[0]:3.2f}|0|2|1.5|{0[1]:3.2f}mA|-128|128|64
3C Catalyst Temperature: Bank 1, Sensor 1|{0:3.0f}°C|-40|6513|10000
3D Catalyst Temperature: Bank 2, Sensor 1|{0:3.0f}°C|-40|6513|10000
3E Catalyst Temperature: Bank 1, Sensor 2|{0:3.0f}°C|-40|6513|10000
3F Catalyst Temperature: Bank 2, Sensor 2|{0:3.0f}°C|-40|6513|10000
40 ! PIDs supported [41 - 60]
41 Monitor status this drive cycle|{0[0]:s}
42 Control module voltage|{0:3.2f}V|0|65.535|14
43 Absolute load value|{0:3.0f}%|0|25700|100
44 Fuel–Air commanded equivalence ratio|{0:3.2f}V|0|2|1.5
45 Relative throttle position|{0:3.0f}%|0|100|90
46 Ambient air temperature|{0:3.0f}°C|-40|215|100
47 Absolute throttle position B|{0:3.0f}%|0|100|90
48 Absolute throttle position C|{0:3.0f}%|0|100|90
49 Accelerator pedal position D|{0:3.0f}%|0|100|90
4A Accelerator pedal position E|{0:3.0f}%|0|100|90
4B Accelerator pedal position F|{0:3.0f}%|0|100|90
4C Commanded throttle actuator|{0:3.0f}%|0|100|90
4D Time run with MIL on|{0:5.0f} minutes|0|65535
4E Time since trouble codes cleared|{0:5.0f} minutes|0|65535
4F Maximum value for Fuel–Air equivalence ratio, oxygen sensor voltage, oxygen sensor current, and intake manifold absolute pressure|{0:3.0f}%|0|255|100|{0:3.0f}%V|0|255|100|{0:3.0f}%mA|0|255|100|{0:3.0f}%kPa|0|2550|1000|{0:3.0f}%|0.8|14|200
50 Maximum value for air flow rate from mass air flow sensor|{0:5.0f} g/s|0|2550|1500
51 Fuel Type|{0[0]:s}
52 Ethanol fuel|{0:3.2f}%|0|100|90
53 Absolute Evap system Vapor Pressure|{0:3.0f}kPa|0|328|200
54 Evap system vapor pressure|{0:3.0f}Pa|-32767|32768|15000
55 Short term secondary oxygen sensor trim, A: bank 1, B: bank 3|{0:3.0f}%|-100|100|50
56 Long term secondary oxygen sensor trim, A: bank 1, B: bank 3|{0:3.0f}%|-100|100|50
57 Short term secondary oxygen sensor trim, A: bank 2, B: bank 4|{0:3.0f}%|-100|100|50
58 Long term secondary oxygen sensor trim, A: bank 2, B: bank 4|{0:3.0f}%|-100|100|50
59 Fuel rail absolute pressure|{0:3.0f}kPa|0|655350|300000
5A Relative accelerator pedal position|{0:3.0f}%|0|100|90
5B Hybrid battery pack remaining life|{0:3.0f}%|0|100|90
5C Engine oil temperature|{0:3.0f}°C|-40|215|100
5D Fuel injection timing|{0:3.0f}°|-210|302|180
5E Engine fuel rate|{0:3.0f}L/h|0|3277|2500
5F Emission requirements to which vehicle is designed|{0[0]:s}
60 ! PIDs supported [61 - 80]
61 Driver's demand engine - percent torque|{0:3.0f}%|-125|125|90
62 Actual engine - percent torque|{0:3.0f}%|-125|125|90
63 Engine reference torque|{0:3.0f}Nm|0|65535|40000
64 Engine percent torque data|{0:3.0f}%|-125|125|90
65 Auxiliary input / output supported|{0[0]:s}
66 Mass air flow sensor|{0[0]:s}
67 Engine coolant temperature|{0:3.0f}°C|-40|215|100
68 Intake air temperature sensor|{0:3.0f}°C|-40|215|100
69 Commanded EGR and EGR Error|{0[0]:s}
6A Commanded Diesel intake air flow control and relative intake air flow position|{0[0]:s}
6B Exhaust gas recirculation temperature|{0:3.0f}°C|-40|215|100
6C Commanded throttle actuator control and relative throttle position|{0[0]:s}
6D Fuel pressure control system|{0[0]:s}
6E Injection pressure control system|{0[0]:s}
6F Turbocharger compressor inlet pressure|{0[0]:s}
70 Boost pressure control|{0[0]:s}
71 Variable Geometry turbo (VGT) control|{0[0]:s}
72 Wastegate control|{0[0]:s}
73 Exhaust pressure|{0[0]:s}
74 Turbocharger RPM|{0[0]:s}
75 Turbocharger temperature|{0:3.0f}°C|-40|215|100
76 Turbocharger temperature|{0:3.0f}°C|-40|215|100
77 Charge air cooler temperature (CACT)|{0:3.0f}°C|-40|215|100
78 Exhaust Gas temperature (EGT) Bank 1|{0:3.0f}°C|-40|215|100
79 Exhaust Gas temperature (EGT) Bank 2|{0:3.0f}°C|-40|215|100
7A Diesel particulate filter (DPF)|{0[0]:s}
7B Diesel particulate filter (DPF)|{0[0]:s}
7C Diesel Particulate filter (DPF) temperature|{0:3.0f}°C|-40|215|100
7D NOx NTE (Not-To-Exceed) control area status|{0[0]:s}
7E PM NTE (Not-To-Exceed) control area status|{0[0]:s}
7F Engine run time|{0[0]:s}
80 ! PIDs supported [81 - A0]
81 Engine run time for Auxiliary Emissions Control Device(AECD)|{0[0]:s}
82 Engine run time for Auxiliary Emissions Control Device(AECD)|{0[0]:s}
83 NOx sensor|{0[0]:s}
84 Manifold surface temperature|{0:3.0f}°C|-40|215|100
85 NOx reagent system|{0[0]:s}
86 Particulate matter (PM) sensor|{0[0]:s}
87 Intake manifold absolute pressure|{0[0]:s}
A0 ! PIDs supported [A1 - C0]
C0 ! PIDs supported [C1 - E0]


Usage
--------
The code has been developed using [Teensy 3][teensy31], the K-line transceiver IC's used were during the development were the [MC33290][mc33290], [SN65HVDA100][SN65HVDA100] and [SN65HVDA195][SN65HVDA195]. All three transceiver IC's worked without problems when the typical application circuit from the datasheet was used. The OBD9141 class itself has been tested on one Kia car build in 2004.

For the Teensy 3.x or LC versions it is recommended to use one of the HardwareSerial ports. For use with Arduino the [AltSoftSerial][altsoftserial] library is used by default. The example `reader_softserial` was tested with an Arduino UNO. The KWP functionality of this library was verified to work on a Teensy 3.5.

A minimal example of how to use the SN65HVDA195 chip mentioned is given by the following schematic:
![Schematic of circuit using SN65HVDA195](/../master/extras/OBD9141_reader/img/OBD9141_reader_cutout.png?raw=true "Schematic of circuit using SN65HVDA195")

The EN pin can either be connected to a pin on the microcontroller or just pulled high in order to always enable the chip.

In the logic folder are some recordings made with a [Saleae logic analyzer][saleae], these show the state of the K-line pin using either a Bluetooth OBD-II reader or this library, these might be useful when developing your own hardware. All timing parameters can be tweaked from the header file, by tuning these parameters, performance of up to 20 requests per second has been achieved (on the same car, 6 readings per second was the maximum with the Bluetooth dongle).

Three examples are given in the example folder. The `reader` and `simulator` examples are to be used with a hardware serial port. The `reader_softserial` example shows how to use it with the [AltSoftSerial][altsoftserial] library. For more information on how to use the library, refer to to the header files.

Timing
------
Several parameters related to timing are given by the specification, some others are beyond our influence. To understand how a request works, lets consider the case the `0x0D` PID is requested, this represents the vehicle's speed.
![Timing diagram of a request](/../master/extras/timing_diagram/timing_diagram.png?raw=true "Timing diagram of a request")

Requesting the value of a PID consists of two phases, the first is the request phase the second the response.

In the first phase, the bytes necessary for the request are written on the Tx line, according to the specification there should be a 5 millisecond delay between each symbol. The duration of this delay is defined by `INTERSYMBOL_WAIT`. It is possible that the ECU still discerns the bytes correctly when this delay is lowered.

The transceiver IC puts the waveform seen on the Tx line on the K-line. However, a echo of this waveform is also provided as output of the transceiver IC and is seen on the Rx of the serial port. Because this is not part of the response we have to deal with this echo. This is done by using the `readBytes` method to read the same number of bytes as were sent during the request. The timeout used for this read is given by (`REQUEST_ECHO_TIMEOUT_MS` * sent_len + `WAIT_FOR_ECHO_TIMEOUT`) milliseconds, where sent_len is the number of bytes sent in the request. Because the serial port used should contain a hardware buffer, very little time is spent in this `readBytes` call, as all the bytes from the echo should already be available and the function returns when the requested number of bytes has been read.

After the echo has been read, the waiting game begins as we wait for the ECU to answer. According to the specification this is atleast 30 milliseconds, this duration (which is the major part of a request duration) is something that cannot be influenced. The timeout set to read the response is given by (`REQUEST_ANSWER_MS_PER_BYTE` * ret_len +  `WAIT_FOR_REQUEST_ANSWER_TIMEOUT`) milliseconds, ret_len represents the number of bytes expected from the ECU. Because this number is known beforehand the `readBytes` method can be used. According to the specification the ECU should also pause between sending the bytes, but this is not necessarily the case.

The number of bytes to be received for each phase is known beforehand so the `readBytes` method can be used; it ensures that we stop reading immediately after the expected amount has been read. The main impact on the performance is given by the time the ECU takes to send a response and the `INTERSYMBOL_WAIT` between the bytes sent on the bus. There is no delay parameter for the minimum duration between two requests, that is up to the user.

Trouble codes
-------------
The library supports reading diagnostic trouble codes from the ECU (the ones associated to the malfunction indicator light). This was made possible with extensive testing by [Produmann](https://github.com/produmann), under [issue #9](https://github.com/iwanders/OBD9141/issues/9).

Contrary to reading the normal OBD PID's, when trouble codes are read from the ECU the length of the answer is not known beforehand. To accomodate this a method is implemented that handles a variable length request to the ECU. In this variable length response, each trouble code is represented by two bytes. These two bytes can then be retrieved from the buffer and converted into a human readable trouble code with letter and 4 digits (for example `P0113`), which can then be printed to the serial port. An example on how to read the diagnostic trouble codes is available, see [`readDTC`](examples/readDTC/readDTC.ino). Increasing the buffer size `OBD9141_BUFFER_SIZE` in the header file may be necessary to accomodate the response from the ECU.

The following trouble-code related modes are supported: Reading stored trouble codes (mode `0x03`), clearing trouble codes (mode `0x04`) and reading pending trouble codes (mode `0x07`).

ISO 14230-2 (KWP)
-----------------
The [ISO 14230-2][KWP] protocol uses the same physical layer as 9141-2, the support for this protocol was developed under [issue #11](https://github.com/iwanders/OBD9141/issues/11). If `initKWP()` is called instead of `init()` the KWP protocol is used for all requests onward. The provided functionality should be the same regardless of the protocol used. A sketch that just tests the KWP functionality is available [`readerKWP`](examples/readerKWP/readerKWP.ino).

License
------
MIT License, see LICENSE.md.

Copyright (c) 2015 Ivor Wanders


[obd2]:https://en.wikipedia.org/wiki/On-board_diagnostics
[teensy31]:http://www.pjrc.com/teensy/
[mc33290]:http://www.freescale.com/products/archived/iso9141-k-line-serial-link-interface:MC33290
[SN65HVDA195]:http://www.ti.com/product/sn65hvda195-q1
[SN65HVDA100]:http://www.ti.com/product/sn65hvda100-q1
[saleae]:https://www.saleae.com/
[altsoftserial]:https://www.pjrc.com/teensy/td_libs_AltSoftSerial.html
[KWP]:https://en.wikipedia.org/wiki/Keyword_Protocol_2000
