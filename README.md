# CYD-Gps-Triple-clock

A ported sketch to use ESP32-2432S028(CYD) showing a GPS clock with Touch Screen.
Aliexpress https://www.aliexpress.com/item/1005006470918908.html?spm=a2g0o.order_list.order_list_main.5.688d1802hXWt5n
https://www.amazon.co.uk/DIYmalls-ESP32-2432S028R-Resistive-ESP-WROOM-32-Development/dp/B0CG2WQGP9?ref_=ast_sto_dp

It has been adapted to attach a small cheap GPS module from Aliexpress to be connected via the CN1 connector on the CYD, no soldering required.

GPS Clock with TFT Display
Author: Bruce E. Hall, Ported by CoolmdXi

Original Source: Bruce E. Hall's GPS Clock https://github.com/bhall66/GPS-clock


Description:
This is a port of Bruce E. Hall's GPS clock sketch for use with a CYD ESP32 2.8" touchscreen module. It displays highly accurate time by syncing with GPS signals. The GPS module is connected through the CN1 connector of the CYD board. The clock features multiple time zones and formats, and allows easy access to GPS-based data like latitude, longitude, and speed.

Features:
GPS-based time synchronization.
Local and UTC time display.
Time format switching (12/24 hour).
Displays location, grid squares, altitude, and speed.
Touch-based interaction for screen switching.
Real-time update from GPS "Pulse Per Second" (PPS) signal.
Hardware Setup:
 ESP32 (CYD Board with 2.8" touchscreen).
GPS Module: Any GPS module with PPS connection
Connect GPS Tx to CYD GPIO 22 (RXD2).
Connect GPS PPS to CYD GPIO 27.
 
Software Requirements:
Arduino IDE version 2.3.2 or later.
ESP32 Board Library version 3.0.4.
Libraries Used:
TFT_eSPI (v2.5.43): For TFT display control.
Time (v1.6.1): For timekeeping.
TinyGPSPlus (v1.1.0): For parsing GPS data.
Timezone (v1.2.4): For managing time zones.
XPT2046_Touchscreen: For touch input.
Key Definitions:
Time Zones:

The sketch is set for British Summer Time (BST) and Greenwich Mean Time (GMT). You can modify this to match your local time zone rules by altering the TimeChangeRule.
TimeChangeRule BST: British Summer Time (UTC+1).
TimeChangeRule GMT: Standard Time (UTC+0).

PPS Support: The sketch uses the Pulse Per Second (PPS) signal for better accuracy. Connect the GPS PPS pin to CYD GPIO 27.

Touchscreen Interactions:
Main Screen:
Displays time, date, location, and grid square.
Tap the time to switch to the GPS data screen.
Tap the location area to switch to the dual time display (local and UTC).
Tap the time zone area to toggle between UTC and local time.
Tap the AM/PM marker to toggle between 12-hour and 24-hour formats.

GPS Data Screen:
Displays latitude, longitude, altitude, speed, and direction.
Tap anywhere to return to the main screen.

Core Functions:
1. showGridSquare:
Computes and displays the current grid square based on the GPS latitude and longitude. This information is typically used by amateur radio operators.
2. locationScreen:
Displays detailed GPS information such as latitude, longitude, altitude, speed, and bearing.
Labels the altitude in feet and the speed in miles per hour.
3. showAltitude:
Displays the current altitude (in feet) as reported by the GPS module.
4. showSpeed:
Displays the current speed (in miles per hour) and direction (in degrees) based on GPS data.
5. dualScreen:
Displays both the local and UTC times in a dual-screen layout.
6. timeScreen:
Displays the main screen with time, date, location, and grid square information.
Includes a status region for satellite count and synchronization status.
7. showTime and showDate:
Displays the current time and date. The time can be shown in either 12-hour or 24-hour format, with an optional AM/PM indicator.
Touchscreen Interactions:
The CYD 2.8" touchscreen allows you to interact with the GPS clock. Below are the available touch interactions:

Time Screen (Screen 0):

Tap on the time to switch to the GPS data screen (Screen 2).
Tap on the location at the bottom right to switch to the dual time screen (Screen 1).
Tap on the time zone to toggle between UTC and local time.
Tap on the AM/PM marker to toggle between 12-hour and 24-hour modes.
Dual Time Screen (Screen 1):

Displays local and UTC time.
Tap anywhere to return to the main screen.
Location Screen (Screen 2):

Displays GPS-based data such as latitude, longitude, altitude, speed, and grid square.
Tap anywhere to return to the main screen.
Time Synchronization:
The sketch uses the GPS module’s Pulse Per Second (PPS) signal to accurately synchronize the time.
If the PPS signal is not available, the sketch can still function, but the time may be less accurate.
GPS Data Handling:
The sketch parses the GPS data using the TinyGPSPlus library to extract useful information like:
Latitude and Longitude.
Altitude and Speed.
Number of satellites visible and course (bearing).
Customizable Settings:
Time Zone: Set up for British Summer Time (BST) and Greenwich Mean Time (GMT). You can modify these settings to match your local time zone by adjusting the TimeChangeRule objects.

Screen Orientation: The screen is set to landscape mode (with the USB on the left). You can modify the orientation by changing the SCREEN_ORIENTATION value.

Touch Calibration:
If needed, fine-tune the touch calibration by modifying the TOUCH_FLIP_X, TOUCH_FLIP_Y, TOUCH_ADJUST_X, and TOUCH_ADJUST_Y values.

For much more detailed information and help for the CYD boards see_ https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display.

Also here is a link to the correct CYD_2usb User_Setup for the TFT_espi library .
https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/DisplayConfig/CYD2USB/User_Setup.h

And a link if you need the standard User_Setup for the single micro USB Board
https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/DisplayConfig/User_Setup.h
