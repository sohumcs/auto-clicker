# Auto Clicker in Python

## Introduction

This Auto Clicker is a Python script designed to automate mouse clicks. It uses the `pynput` library to control the mouse and listen for keyboard events, allowing the user to start and stop the clicking process with a toggle key. The script continuously clicks the left mouse button at a very high frequency until toggled off.

## Features

- **Automate Mouse Clicks**: Perform left mouse button clicks.
- **Toggle Control**: Start and stop the auto-clicking process with a specific key press.
- **High Frequency Clicking**: Clicks at a very high frequency (approximately every 1 millisecond).
- **Multithreading**: Utilizes multithreading to handle mouse clicking and keyboard listening concurrently.
- **Cross-Platform**: Works on Windows, macOS, and Linux.

## Requirements

To run the auto-clicker, you need to have Python installed on your machine along with the `pynput` library. You can install `pynput` using pip:

```sh
pip install pynput
