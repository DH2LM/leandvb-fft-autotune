# leandvb-fft-autotune
A script by Martin DH1DF and me for LeanDVB to automatically tune into found stations.


### About
These scripts allow you to automatically tune into QO-100 DATV stations via LeanDVB. It was originally written by Martin DH1DF and extended by a few functions by me.


### Installing
#### Dependencies
- An Installation of [LeanDVB](http://www.pabr.org/radio/leandvb/leandvb.en.html)
- Python3 and Python3-Websockets to run the script properly
```
sudo apt-get update && sudo apt-get upgrade
sudo apt install python3 python3-pip python3-websockets
```


#### The Easy Way
TBA


#### The Hard Way
- Install [LeanDVB](http://www.pabr.org/radio/leandvb/leandvb.en.html). ```/home/your-user-name/leandvb/src/apps``` Should be the directory where the built applications are located.

- Install the remaining dependencies:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt install python3 python3-pip python3-websockets
```

- Clone both scripts 
```cd ~ && git clone https://github.com/creepebrine/leandvb-fft-autotune```
You now can find them under /home/your-user-name/leandvb-fft-autotune.


### Usage

#### How to use both scripts
Both scripts can be used using the following commands and arguments:
```
./fft 0

or

./fft-modgui 0 0 0


- where the first Argument describes how many stations will be skipped; (0 = beacon, 1 = first after beacon, ...)

- (modgui only) the second argument toggles the GUI (0 = off, 1 = on)

- (modgui only) the thrid argument enables/disables recording of the output (0 = off, 1 = TS output, 2 = RAW IQ)
```

To switch to the next station, simply close the XTerm Window the script automatically opens. To quit, CTRL+C the Python Script.


#### Examples

##### Receiving and recording the beacon
Use the fft-modgui script for this example. Since the beacon is the first station the script will read, there is no need to skip any station. For best performance, disable GUI. You have to use the third argument "1" to enable recording to the file ```/home/your-user-name/out-datetime.ts```. The Command you need looks like this:
```
./fft-modgui 0 0 1
```

##### Receiving the second DATV station after the beacon with GUI and no recording
Use the fft script for this example, since you want to use the GUI and you do not want to record anything. Furthermore you want to jump to the second station after the beacon, so your first argument you have to set is "2".
```
./fft 2
```


### Necessary Adjustments
Since every LNB has a different drift, you might have to adjust the drift. Use the GUI and a rather narrow station (if available) to crudely determine the needed offset using the signal's bandwith and the fact that if your signal is left of the middle your frequency is too low and vice versa. To adjust the offset, open the scripts with your favourite editor and search for the line that starts with ```cmd=```. Look for ```rtl_sdr -f``` in that particular line. There you will find the formula to determine the frequency: ```((freq)*1000+offset)```. Change the offset the way you need it.


### To be added // TBA
automatic refresh of the frequency list
optional arguments
manual station / GUI / record switching
