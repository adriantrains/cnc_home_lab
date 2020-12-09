# **CNC HOME LAB**

During the pandemic there was a need for a small, easy-to-use CNC at home. For this, at the Fab Lab León we have decided to use the SainSmart Genmitsu CNC Router 3018-PRO DIY Kit model.

[Sainsmart CNC](https://www.sainsmart.com/products/sainsmart-genmitsu-cnc-router-3018-pro-diy-kit)

**Assembly:**
Following the manufacturer's steps, you should look at these that are the most important. These are the materials.

![](https://i.imgur.com/wKPmRac.jpg)


**1.** When assembling the structure, we will not tighten the screws until the end. The gray pieces where the aluminum sacrificial board will sit must be placed opposite as in the image. The motor coupling and the threaded rod must have a gap of 2 mm with the motor. Important the position of the golden piece and the spring.

![](https://i.imgur.com/lHRJ6FP.jpg)

![](https://i.imgur.com/UdP0DpA.jpg)

![](https://i.imgur.com/y8OIuDE.jpg)

**2.** In the lateral profiles we will introduce the nuts to hold the vertical sides. We will leave the distance of 2 cm apart.

![](https://i.imgur.com/YIRxgvH.jpg)

**3.** We will put the second golden piece and the spring on the threaded rod in the spindle holder. 

![](https://i.imgur.com/zGWGpHY.jpg)

**4.** We will place the nuts to hold the electronic board on the back of the extruded profiles.

![](https://i.imgur.com/xPSuocI.jpg)

**5.** At the time of putting the spindle to hold the threaded rod to the motor shaft, we will leave the 2 mm gap again.

![](https://i.imgur.com/fLKVjof.jpg)

**6.** It is important to place the spacers to isolate the electronic board.

![](https://i.imgur.com/aw4Iy4l.jpg)

**7.** We will order the cables. 

![](https://i.imgur.com/fZOXMmG.jpg)


**INSTALLATION AND CONFIGURATION**

1. We need to install the CH340 driver.
2. We will execute the GRBL Control and in Settings we will update the communication port. **Important** if the machine is connected to the remote control it will not work from the computer. For MAC you can follow this tutorial:
[GRBL Candle for Mac](https://docs.sainsmart.com/article/zcyhab7a0k-how-to-install-grblcontrol-candle-for-mac)
3. **IMPORTANT:** Some of the motors may be inverted, for this we will modify the GRBL configuration. Through this *$$* command we will identify what values the GRBL has. In the value *$ 3 = ??* We will have to review the table of the following [link](https://github.com/gnea/grbl/wiki/Grbl-v1.1-Configuration#3--direction-port-invert-mask) to see what value we need to change.
4. We will adjust the Zero XY and Zero Z. We will load a file extension .nc
5. In **Fab Modules** we can generate a .nc file using the **Othermill** program. 
6. In **Mods** we will create it using the **GCODE mill 2D PCB png** program.

We have followed [Jacopo Di Matteo's](http://fabacademy.org/2019/labs/waag/students/jacopo-dimatteo/assignments/week05/) documentation which includes a Mods module for mills in V.

This is the result.
![](https://i.imgur.com/JYk7TFk.jpg)

**MORE INFORMATION**

[Sainsmart Wiki](http://wiki.sainsmart.com/index.php/101-60-280PRO)
