# wavelogger
## Measure and / or log 4 channel Volt (V), Current (I) and Power (P) readings with a WaveShare Current / Power Monitor HAT on a Raspberry Pi.
The output format of the logging script has been optimised for a Comma Separated Value (CSV) format that may easily be imported to Microsoft Excel for further analysis or graphing.
## The manufacturer link to the WaveShare Current / Power Monitor HAT is here:
https://www.waveshare.com/current-power-monitor-hat.htm
## The HAT is available in South Africa through the following link:
https://www.robotics.org.za/W17539?search=W17539
### Example of a WaveShare HAT mounted on a Raspberry Pi Zero W with probes connected.
![WaveShare HAT on Raspberry Pi Zero W with probes connected](https://github.com/ZS6TVB/wavelogger/blob/main/img/waveshare_hat_pizerow.png)
### Example connection diagram of the WaveShare HAT, connected to a load to measure V, I and P on one channel.
![Wiring Diagram - Connection on one channel](https://github.com/ZS6TVB/wavelogger/blob/main/img/waveshare_wiring_diagram.png)


## Prerequisites (Before executing the logging script).
#### 1. Enable I2C on the Raspberry Pi

In a terminal on the Rasperry Pi, run:

`sudo raspi-config`

Choose: 

`3 Interface Options  -->  P5 I2c  -->  YES  --> OK  --> Finish`


#### 2. Upgrade your Raspberry Pi and Install git, SMBUS for Python3

In a terminal on the Raspberry Pi, run:

`sudo apt update && sudo apt upgrade -y && sudo apt -y install python3-smbus git`

## Installation on a Raspberry Pi
Installation is extremely simple.  There is only one Python3 script named `wavelogger.py`.  To install the script, copy or downoad it to a directory on your Raspberry Pi or clone it from this git repository.

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

To log to a file to be imported into Microsoft Excel, execute wavelogger in a terminal as shown in the following example:

`cd ~/wavelogger`

`./wavelogger.py > examplelogfile.csv`

Should you wish to display the output of the log file whilst logging, in another terminal on the same Raspberry Pi, execute the following commands:

`cd ~/wavelogger`

`tail -f examplelogfile.csv`

Press ^c to exit.

To stop logging, return to the original terminal where wavelogger.py was originally executed executed and press ^c.

## Importing to Microsoft Excel
To import your logs to Microsoft Excel for further analysis or graphing, simply transfer the log file e.g. examplelogfile.csv to the PC where Microsoft Excel is installed and open it in Excel.

## Log sample rate
By default, the log sample rate of the wavelogger.py script has been configured to take one sample every second.  The sample rate is determined by the `time.sleep(1)` variable on the second last line in the script.  In order to change the sampling rate, simply use your favourite editor and change the parameter to suit your needs.  The following examples should provide a guideline of how to configure the `time.sleep(1)` value for the sample rates required.


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



