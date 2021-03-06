# wavelogger
## Measure and log 4 channels Volt (V), Current (I) and Power (P) measurements with a WaveShare Current / Power Monitor HAT on a Raspberry Pi
The output format of the logging script has been optimised for a Comma Separated Value (CSV) format that may be easily imported into Microsoft Excel for further analysis or graphing.

The WaveShare HAT INA219 chips are configured to measure a maximum voltage of 32V whilst the configured maximum current is 2A (allowing that the probes and probe wires connected to the HAT can handle 2A).


## The manufacturer link to the WaveShare Current / Power Monitor HAT is:
https://www.waveshare.com/current-power-monitor-hat.htm
##  

## The HAT is available in South Africa through the following link:
https://www.robotics.org.za/W17539?search=W17539
##  

## Probes and probe wires were obtained from my friendly local electronics store:
https://electronicsfg.co.za/
##  

### Example of a WaveShare HAT mounted on a Raspberry Pi Zero W with probes on all four channels
![WaveShare HAT on Raspberry Pi Zero W with probes connected](https://github.com/ZS6TVB/wavelogger/blob/main/img/waveshare_hat_pizerow.png)
### Example connection diagram. The WaveShare HAT is connected to a load to measure V, I and P on one channel
![Wiring Diagram - Connection on one channel](https://github.com/ZS6TVB/wavelogger/blob/main/img/waveshare_wiring_diagram.png)


## Prerequisites (Before executing the logging script)
#### 1. Enable I2C on the Raspberry Pi

In a terminal on the Rasperry Pi, run:

`sudo raspi-config`

Choose: 

`3 Interface Options  >>  P5 I2c  >>  YES  >> OK  >> Finish`


#### 2. Upgrade your Raspberry Pi, install git and SMBUS for Python3

In a terminal on the Raspberry Pi, run:

`sudo apt update && sudo apt upgrade -y && sudo apt -y install python3-smbus git`

## Installation on a Raspberry Pi
Installation is simple.  There is only one Python3 script named `wavelogger.py`.  To install the script, copy or downoad it to a directory on your Raspberry Pi or clone it from this git repository.

To clone the script to your Raspberry Pi using git, run the following commands in a terminal on your Raspberry Pi:

`cd`

`git clone https://github.com/ZS6TVB/wavelogger`

`cd ~/wavelogger`

Before execution of the wavelogger script, ensure it has execution rights:

`chmod +x wavelogger.py`

## Execution of wavelogger.py
The script was designed to output Microsoft Excel compatible files on the terminal where it is executed from.  To execute the script and output measurements to the terminal, run the following example commands in a terminal: 

`cd ~/wavelogger`

`./wavelogger.py`

To log to a file for later import into Microsoft Excel, execute wavelogger in a terminal as shown in the following example:

`cd ~/wavelogger`

`./wavelogger.py > examplelogfile.csv`

Should you wish to display the output of the log file whilst logging, in another terminal on the same Raspberry Pi, execute the following commands:

`cd ~/wavelogger`

`tail -f examplelogfile.csv`

Press ^c to exit.

To stop logging, return to the original terminal where wavelogger.py was originally executed and press ^c.

## Importing into Microsoft Excel
To import your logs to Microsoft Excel for graphing or further analysis, simply transfer the log file e.g. examplelogfile.csv to the PC where Microsoft Excel is installed and open it in Excel.

## Sample rate
By default, the sample rate of the wavelogger.py script has been configured to take one sample every second.  The sample rate is determined by the `time.sleep(1)` value on the second last line in the script.  In order to change the sample rate, simply use your favourite editor and change the parameter to suit your needs.  The following examples should provide a guideline of how to configure the `time.sleep(1)` value for the sample rates best suited to your needs.


Sample once every second (default behaviour):

`time.sleep(1)`


Sample once per minute:

`time.sleep(60)`


Sample once every 30 seconds:

`time.sleep(30)`


Sample 4 times every second:

`time.sleep(.25)`


Sample twice per second:

`time.sleep(.5)`



