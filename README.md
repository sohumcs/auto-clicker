Auto Clicker in Python
Introduction
This Auto Clicker is a Python script designed to automate mouse clicks. It uses the pynput library to control the mouse and listen for keyboard events, allowing the user to start and stop the clicking process with a toggle key. The script continuously clicks the left mouse button at a very high frequency until toggled off.

Features
Automate Mouse Clicks: Perform left mouse button clicks.
Toggle Control: Start and stop the auto-clicking process with a specific key press.
High Frequency Clicking: Clicks at a very high frequency (approximately every 1 millisecond).
Multithreading: Utilizes multithreading to handle mouse clicking and keyboard listening concurrently.
Cross-Platform: Works on Windows, macOS, and Linux.
Requirements
To run the auto-clicker, you need to have Python installed on your machine along with the pynput library. You can install pynput using pip:

sh
Copy code
pip install pynput
Script Overview
Here is the complete Python code for the auto-clicker:

python
Copy code
import time
import threading 
from pynput.mouse import Controller, Button
from pynput.keyboard import Listener, KeyCode

TOGGLE_KEY = KeyCode(char="*")

clicking = False
mouse = Controller()

def clicker():
    while True:
        if clicking:
            mouse.click(Button.left, 1)
            time.sleep(0.001)

def toggle_event(key):
    if key == TOGGLE_KEY:
        global clicking
        clicking = not clicking

click_thread = threading.Thread(target=clicker)
click_thread.start()

with Listener(on_press=toggle_event) as listener:
    listener.join()
Detailed Explanation
Imports:

time: For adding delays between clicks.
threading: For running the clicking process in a separate thread.
pynput.mouse: To control the mouse.
pynput.keyboard: To listen for keyboard events.
python
Copy code
import time
import threading
from pynput.mouse import Controller, Button
from pynput.keyboard import Listener, KeyCode
Constants and Global Variables:

TOGGLE_KEY: The key used to toggle the clicking on and off. In this case, it is the * key.
clicking: A boolean variable that tracks whether the clicking is active.
mouse: An instance of Controller to control the mouse.
python
Copy code
TOGGLE_KEY = KeyCode(char="*")
clicking = False
mouse = Controller()
Clicker Function:

This function runs in a loop and clicks the left mouse button if clicking is True.
python
Copy code
def clicker():
    while True:
        if clicking:
            mouse.click(Button.left, 1)
            time.sleep(0.001)
Toggle Event Function:

This function toggles the clicking state whenever the TOGGLE_KEY is pressed.
python
Copy code
def toggle_event(key):
    if key == TOGGLE_KEY:
        global clicking
        clicking = not clicking
Starting the Clicker Thread:

The clicker function is started in a separate thread to allow concurrent execution with the keyboard listener.
python
Copy code
click_thread = threading.Thread(target=clicker)
click_thread.start()
Keyboard Listener:

A Listener is set up to listen for the TOGGLE_KEY press and toggle the clicking state.
python
Copy code
with Listener(on_press=toggle_event) as listener:
    listener.join()
Usage
Clone the Repository:
Clone the repository from GitHub to your local machine.

sh
Copy code
git clone https://github.com/sohumcs/auto-clicker.git
cd auto-clicker
Install Dependencies:
Install the required dependencies using pip.

sh
Copy code
pip install pynput
Run the Script:
Execute the script using Python.

sh
Copy code
python auto-clicker.py
Start/Stop Clicking:

Press the * key to start the auto-clicking.
Press the * key again to stop the auto-clicking.
Example
Here’s an example of how to use the script:

Run the script:

sh
Copy code
python auto-clicker.py
Press the * key to start the auto-clicking.

Press the * key again to stop the auto-clicking.

Conclusion
This Auto Clicker script provides a simple yet powerful way to automate mouse clicks with a toggle key for easy control. By using Python and the pynput library, the script is flexible and can be adapted for various automation tasks.
