# Heat_Meter
ECE project to measure surface tempeture and control a fan speed to cooldown the system

the full project based on many stages from measuring the tempereture to fan speed <br>
**all stages shoown in the diagram**

### <br>
roject roadmap :
1- measure tempereture  <br>
2- maping the tempereture  <br>
3- using the controoler  <br>
4- controol code the fan <br>
 <br>


## 1- sensing the tempereture:
> for sensing the temperetur ewe use IC  ***LM35*** 

|**Feature**| **value** |
|-----------|----------|
|supply voltage| 4V ~ 30V | 
|output voltage| 1.5V |
|sensitive| 9.8 mV//C |

the sensor measure the serface tempeteure and return a maximum value of ~ 1.5V  <br>
this value is very small and canot measured by the controoler so we have to map the voltage value to highter value this take us to the next step.
<br><br>
## 2- maping the tempereture:
--

most controllers read *5V* values so we need to map the *1.5V* to *5V*<br>

we will ues ***opamp 741*** to map this value using ***non inverting amplifier*** .
in ***ideal non inverting amplifier*** the gain can be calculating using 



in our cause 



so the ratio between Rf and R1 eqal to 
our resistors values is 



then the connecton as in fig 



then the output of the opamp ready to inter the arduino


##3- using the controoler
> in heis section we usen arduino uno R3 

here we read volte in range ( 0V ~ 5V) "which referance on the tempereture"  as analog values "in the arduino" in 10-bit range ( 0 ~ 1023)

we take this value and map it again in PWM 8-bit range ( 0 ~ 255) and use it to controol:<br>
1- fan speed <br>
2- RGB led  <br>

the RGB led  should refer to 2 thinsg:<br>
1- tempeteure value (when tempereture increase the led move from blue to red )<br>
2- fan speed (when the fan speed increase the RGB move from blue to red) <br>
