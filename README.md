# X-56 HOTAS I/O Tools
I/O tool for debouncing &amp; repeating X-56 Hands-On Throttle input.

## What it does...
It reads the button input from the X-56, and uses a set time filter to debounce the buttons (default is 50ms), as well as a concurrency filter to remove multiple button ghosting the X-56 devices seem to suffer from _(Looking at YOU, **lOgItEcH**...)_.

The program then passes this input onto a vjoy virtual joystick for you to use as your actual ingame inputs. 

## Dependencies
### Python3
The program runs on [Python3](https://www.python.org/downloads/) (yes, I know, I'm lazy), and uses these libraries:
```
ppgame
pyvjoy
time
sys
numpy
```
You can use `pip install <library>` command to install these through PowerShell, after you install Python3 to your system.

### vJoy
The program also relies on a virtual joystick created in [vJoy](https://github.com/shauleiz/vJoy). You need to create a 36 button device with no axes. You can learn more about how to do this [here](http://vjoystick.sourceforge.net/joomla/index.php/dev/88). 

## How to run...
### Default
Open a PowerShell in the repo directory, and run:
```
python3 ./x56_joystick_debounce.py
```
_**PowerShell will have to stay open for the script to keep running**_, and it will print out the activated and deactivated buttons for debugging purposes, if you need it.

### Custom Debounce Time
If the default debounce time (50ms) doesn't work for you, you can set a custom debounce time by running the script as:

```
python3 ./x56_joystick_debounce.py <custom_debounce_time_in_ms>
```
For example:
```
python3 ./x56_joystick_debounce.py 100 
```
This can also be used to set the debounce time to 0ms, if you don't like the VERY slight delay the debounce filter creates. Note that setting the custom time to 0 will DISABLE DEBOUNCING.

## Additional Notes
- The scroll wheel on the HOTAS is not passed through the debouncing filter. They will print with `(UNFILTERED)` warning next to them, but you can still assign them through the virtual joystick.
- If the physical device is ever disconnected while this program is running, this program will stop and will need to be rerun.
- This script only passes BUTTONS through... You will still need to use the original axes from the X-56 Throttle ingame. I may whip up an axis passthrough in the future, but for now, this is it.
