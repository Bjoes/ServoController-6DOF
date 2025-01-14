# ServoController-6DOF
ATMEGA2560 Servo controller for use with FlyPT mover and AASD-15A drives

600mm travel actuator with SF1610 ball screw
Scale = 0.9155

2 arduino mega are needed, each controlling 3 servoes. This is due to the mega only have 4 16 bit timers. 
Therefore we can only control 4 servoes pr arduino in 16bit resolution.
We will then have 2 channels leftover on each arduino which can be used for seatbelt tensioner etc.

```
flypt settings for first output
"<255><255><a1><a2><a3><0><0>"

flypt settings for second output
"<255><255><a4><a5><a6><0><0>"

In case you wanna use the last 2 axis you could replace <0><0> in both strings with <a7> and <a8> to have 8 axis.
```
```
Pn2 = 2
Pn8 = 300
Pn9 = -300
Pn51 = 3000 (motor top speed/rpm, could be run slower if wanted)
Pn98 = 10
Pn109 = 1
Pn110 = 30
Pn113 = 20
Pn114 = 10
Pn115 = 100
Extra parameters needed in the AASD-15A drivers used for limits detection:
Pn24 = 100 (reach predetermined torque > 100%)
Pn52 = 1
Pn60 = 2 (not used for now)
Pn61 = 6

AASD-15A CN2 DB25 control signal connector explained:
 p3 - pwm signal
 p4 - direction
 p5 - GND
 p6 - enable (motor ON) - Break this connection to stop motors (e-stop)
 p9 - 5Vcc
p10 - GND
p11 - ready (motor present and ready - not used for now)
p14 - GND
p23 - torque reached (not used)

AASD-15A
CN2 DB25 pin / Arduino pin
Motor 1
 3              12
 4              30
 6              GND
 #23            18 (via 2.2kohm resistor and 0.1uF capacitor to GND)
 9              5Vcc
 5,10,14        GND
 11             A8

Motor 2
 3              2
 4              31
 6              GND
 #23            19 (via 2.2kohm resistor and 0.1uF capacitor to GND)
 9              5Vcc
 5,10,14        GND
 11             A9

Motor 3
 3              7
 4              32
 6              GND
 #23            20 (via 2.2kohm resistor and 0.1uF capacitor to GND)
 9              5Vcc
 5,10,14        GND
 11             A10

Motor 4
 3              45
 4              33
 6              GND
 #23             21 (via 2.2kohm resistor and 0.1uF capacitor to GND)
 9              5Vcc
 5,10,14        GND
 11             A11
```

```
DB25
3 = Blue
4 = Brown
5 = Brown/white
6 = Green
9 = Orange
10 = Blue/white
14 = Green/white
11 = Orange/white

GX16 8 PIN
1 = Blue
2 = Brown
3 = Brown/white
4 = Green
5 = Orange
6 = Blue/white
7 = Green/white
8 = Orange/white
```
