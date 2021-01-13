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
3. We will adjust the Zero XY and Zero Z. We will load a file extension .nc
4. **IMPORTANT:** Some of the motors may be inverted, for this we will modify the GRBL configuration. Through this "$$""  command we will identify what values the GRBL has. In the value "$ 3 = ??"" We will have to review the table of the following [link](https://github.com/gnea/grbl/wiki/Grbl-v1.1-Configuration#3--direction-port-invert-mask) to see what value we need to change.


# 2.5D STL (MOLDING AND CASTING)

1. In **Mods** we will create it using the **GCODE mill 2.5D stl** program.
2. If we vary the value in the offset number (0.8) or the offset setpower (0.5) we will achieve a finer or coarser milling. Remember to put in mm. The cut speed 25 mm/s.
3. Then with the **Shopbot mill 3D** module, we will have to change the module at the end for one that generates the GCODE. The Stepover will be 0.2 and with a flat end mill.Cut speed 2.5 mm/s.

![](https://i.imgur.com/eIg2XR7.png)


4. This is the result.

![](https://i.imgur.com/why4d9c.jpg)


# PCB PRODUCTION

1. In **Fab Modules** we can generate a .nc file using the **Othermill** program. 
2. In **Mods** we will create it using the **GCODE mill 2D PCB png** program.


We have followed [Jacopo Di Matteo's](http://fabacademy.org/2019/labs/waag/students/jacopo-dimatteo/assignments/week05/) documentation which includes a Mods module for mills in V.

This is the result.

![](https://i.imgur.com/JYk7TFk.jpg)

# Z PROBE IN CNC 3018 / 1810

If you are using some of the Sainsmart small CNC, you will realize that there is no Z axis automatic home, you have to make Z home by hand. No good for those who wants to make beautiful pcb boards without many effort.

You can find the official Sainsmart tutorial in this link:
https://docs.sainsmart.com/article/yhgowhcb8x-what-is-a-z-probe-how-do-i-use-it

You can buy the Z-Probe tool (if your machine comes without, usual in standard kits):
https://www.sainsmart.com/collections/genmitsu-cnc/products/sainsmart-cnc-router-z-axis-tool-setting-touch-probe

But, you can make your OWN ZPROBE for the Sainsmart 3018/1810 and connect to the Board and use it for ZProbe and also to make a Heightmap of the piece you want to mill (particullary useful to make pcb).

# MAKE YOUR OWN ZPROBE.

You will need:

- **Dupont female 2x connector cable**: You can make your own, get one from prototiping cables or use one from electronic scrap (pc internal button or something like this)
 ![](https://i.imgur.com/POKYGVW.png)
 - **1 alligator cable** usually found in electronic stores or something like that.
 - ![](https://i.imgur.com/E8acEXe.png)
 - **1 washer medium size** this is for a second hack
 - **Soldering iron and soldering wire.**

Now with all this stuff, you must make a cable that has two wire, with the dupont connectors in one side and two alligators (or an alligator and a washer) in the other side.

Final images with the cable, with and without washer.

Without washer:
![](https://i.imgur.com/2qTrjJh.jpg)
With Washer:
![](https://i.imgur.com/k10Fo2L.jpg)

## TESTING CONTINUTY

Its important to test the cable, because we will use this to make a close loop in the A5 pin, and if the cable is not well made, you can traspass the board, so lets tes the cable:
![](https://i.imgur.com/25LEmvQ.jpg)


Now test the washer. Sometimes washers come with a coating, and you must sand it a little bit to get to the metalic part
![](https://i.imgur.com/q8Yt5NF.jpg)

If you get the continuity, thats good.
Now lets go to the use of this cable.

## INSTALLATION 

Now lets install this cable in the machine.

The Z Probe cable we have just made must be installed in the A5 pin in the controller board. The GND pin is marked in the board.
![](https://i.imgur.com/hgJ8msS.jpg)
If you have other board, not exactly this one (from CNCpro version) you just find the A5 text in the board:
![](https://i.imgur.com/82OmnZV.jpg)

So now connect the cable to the A5 pin with the dupont connector. And thats all :)
![](https://i.imgur.com/AQIuNeZ.jpg)

Now the alligator clip (no matter if its positive or negative) should "biting" the bit:
![](https://i.imgur.com/3Tec7AQ.png)


and the other cable should be touching the surface of the board you will mill. 

You can use the alligator finish if you have a pcb holder
With alligator (if you have space down the board):
![](https://i.imgur.com/FO14c7a.jpg)

or you can use the washer to tape it to the surface of the board, if you have no space to use the alligator in the pcb board.
Or using the washer, if you use double side tape to fix the board to the bed:
![](https://i.imgur.com/PhdONjA.jpg)

**IMPORTANT**: check conductivity again, if you can, to see if the circuit will be closed when you operate with the machine.

## CONFIGURE Z PROBE IN CANDLE SOFTWARE

Once you have all the settings (A5 pin in the CNC board with the cable, one alligator in the bit and the other cable in the pcb copper board) lets probe the settings in Candle software (Link to the software git: https://github.com/Denvi/Candle)

Open candle and connect to the machine through USB. 
Now move the spindle to a XY possition where there is copper in the PCB, and then push the ZProbe button in the software:
![](https://i.imgur.com/87a263E.png)

After you click it, the Spindle will go down to contact the board. When the bit touches the board, it must go up again and stablish the Z=0 for this job.

### WARNING: If the bit still going down after touching the PCB board, that means that there is no conductivity in the cable (maybe the washer is not touching well the surface, or the alligator is not properly hanged to metal part)
### Use the "PAUSE" button to STOP the movement, and then the "ABORT" button to make the spindle go up.
![](https://i.imgur.com/p5X4AmJ.png)




# MAKE A HEIGHTMAP OF THE PCB BOARD

Update by Pablo Nuñez.

Now if you have a big job, and you have some issues in the pcb milling (some parts mill, others not) you need to make a heightmap of your board before mill it.
![Image from Sainsmart website](https://i.imgur.com/icAFkiF.png)


This means that automatically the machine will make several ZProbe (similar than we did before with the cable), but will store an array of heights. The the machine will adapt the milling process to this array of Z values, so the board will mill perfectly.

Check the Sainsmart tutorial if you want: https://docs.sainsmart.com/article/kj4xzak19j-how-to-utilize-height-mapping-in-candle

I will explain my workflow here, but i followed this.

First you need a cable for Z Probe (the one we did in the other section), and attach it to A5 pin. Then put one side of the cable to the mill and the other to the pcb (review the last section if you have doubts)

After we open the Candle software and activate the Heightmap option in the menú Service -> Settings -> Console section -> Activate Heightmap:

![](https://i.imgur.com/exmpje9.png)


Then OK 


Now move the XY position to the lower-left point in the PCB, and press the XY=0 button. 
![](https://i.imgur.com/ALozEfl.png)

Also you can test the ZProbe, and make a Z=0 automatically (check the pause button, be careful with this, stay alert).
So now we have zeroed everything, move down the spindle until it is close to the board, 1 mm above it. (Dont do Z=0)

In the right panel, after the control part, now we have a Heighmap section. Press the three lines to expand it.
Now press the button CREATE in this section:
![](https://i.imgur.com/3Fsag6s.png)

NOw press the button AUTO, so the Heighmap suface will be equal than the board you want to mill:
![](https://i.imgur.com/Bleeptl.png)

Now lets decide how many "probes" will make in the X axis and in the Y axis. As the website says, check the extension of the board and divide the mm / 10. For example:
![](https://i.imgur.com/E7ct5mf.png)

So: 
X= 36mm
Y= 12mm

divided by 10 we have X=3 and Y=1 (actually we must use Y=2, because is the minimum value). So this is the number of probes we want to make in this board in each axis. Now write this values in the "PROBE GRID" part:

![](https://i.imgur.com/zvexVHs.png)

And as wee see, the table in the middle show the values we updated. We can add some X or Y point to probe, if we think we need more.

Now we go to the phisical part.
To start measuring the Heightmap, you have a button in the lower part of the Candle, "PROBE". When you press it the machine will start touching the board, in the first point, and then goes up, move to the next point, and down again....it will repeat until the points we configure to make the height map are finished.

**KEEP AN EYE IN THE MACHINE, and stay alert to press the "PAUSE" button or the "ABORT" button, if the mill goues through the pcb because there is a bad conductivity in the cable.**
![](https://i.imgur.com/5qhHpiR.png)

When finished, all the data in the table will be filled with heights, and in the pcb draw you will have different colours. The more colours, the more difference in the height of each point.

Now press the button "EDIT MODE" in the right panel to finish the heighmap data collection.
![](https://i.imgur.com/uVunCs2.png)


Now you can send the job as usual. The machine will adapt to the heigh of each point through the board.

![](https://i.imgur.com/9jUl3dx.jpg)


# FAQ

- In the "PROBE" button there is an ALARM Signal and is in RED....im in panic!
    - OK, calm down. It means that, when the machine was making a probe in some point, moves in the Z axis more than the "security distance" to make the probe. Now you need to abort the process, ans start again. You can increase this security distance in the Zb parameter in the heighmap panel.
    - ![](https://i.imgur.com/BwvaYFq.png)




**MORE INFORMATION**

[Sainsmart Wiki](http://wiki.sainsmart.com/index.php/101-60-280PRO)


