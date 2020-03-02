## Smart Services summer project: Algae Growth Monitoring
The main purpose of this project is to help researchers keep track of natural conditions in the pool for 
algae cultivation.
What I have created: 
- Create an IoT system for monitoring algae growth factor( light, temperature, pH) 24/7, publishing these data to cloud using MQTT protocol. 
- Create a local website for calibrating pH probe with instruction and good UI

The system circuit:

<img src = "https://user-images.githubusercontent.com/32799668/75661459-064fa280-5c76-11ea-93fa-31cb0b0f8174.png" width = "300">

### More details: 
#### 1) Data monitoring using Grafana:

<img src="https://user-images.githubusercontent.com/32799668/75659668-0e5a1300-5c73-11ea-803f-8d923514984d.png" width="400">
<img src="https://user-images.githubusercontent.com/32799668/75661910-dce34680-5c76-11ea-8f2f-027852b25724.png" width="400">

#### 2) Calibrating pH probe via web interface:
EZOTM circuit enables users to write commands to get what they want, such as “Cal,mid,n” for middle point calibration, or “R” for reading pH value. An Atlas-Scientific team has released a sample code to make sending commands to the circuit in I2C mode possible. This is the link to the sample code written in Python made specifically for Raspberry Pi:  
https://github.com/AtlasScientific/Raspberry-Pi-sample-code/blob/master/i2c.py 
Since equation for pH reading is not linear, it is a must to perform three-point calibration with 3 buffer solutions in the kit. The commands are: “Cal,low,4”; “Cal,mid,7” and “Cal,high,10”. To simplify the task, a good user interface and instruction are required:

<img src = "https://user-images.githubusercontent.com/32799668/75660722-c1773c00-5c74-11ea-8f17-6f67436847ad.png" width = "700" >
After the submit button is pressed, the Node.Js app will capture the information and send it to Python main program via a socket. The calibration process is performed, and via I2C protocol, Python gets the calibration status.
If calibrating is successful, there will be a green successful message. Otherwise, the error message will pop up.


<img src = "https://user-images.githubusercontent.com/32799668/75662505-e0c39880-5c77-11ea-92a1-5b59815be581.png" width = 500>
<img src = "https://user-images.githubusercontent.com/32799668/75662607-0a7cbf80-5c78-11ea-8ac3-052af3869e17.png" width = 500>



### References:
- https://github.com/ControlEverythingCommunity/TSL2561
- https://github.com/steve71/MAX31865
- https://github.com/AtlasScientific/Raspberry-Pi-sample-code/blob/master/i2c.py
- https://github.com/adafruit/Adafruit_Python_ADS1x15
