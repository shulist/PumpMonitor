# Program to monitor 2 sump pumps
#### The objective ####
This program is to monitor two pumps, ** pumpW ** & ** pumpE **. Each pump operates independently. Each pump has a float switch which is triggered when the water level in the sump reaches a certain predetermined upper level. When the switch triggers it sends a 12 volt signal to an optocoupler isolation board. This board then forwards a 3.3 volt signal to the Raspbery Pi sending one of the GPIO pins 'High' when the pump cycle finishes the float switch drops below the lower threshold level and cuts off the 12 volt signal and ultimately removes the 3.3 volt signal.

#### The Raspberry Pi ####
Will do the following:
1. Monitor for the signal to go 'High' on either GPIO.
2. Record the pump name = pumpX (pumpW or pumpE)
3. Record the Date-Time the signal went 'High' = dateTime (yyyy-mm-dd HH:MM:SS)
4. When one of the signals goes from 'Low' to 'High' start a timer. = pumpXRunTime (mm:ss)
5. When the signal drops back to low stop the timer.
6. Send the MQTT broker a message containing the 
```pumpX, dateTime, pumpXRunTime.```
7. Return to step 1 above
