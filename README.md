ChronoGraph: Embedded Linux Visualization System
Embedded Python visualization system featuring a custom time-to-coordinate mapping algorithm for a constrained SPI display.

⚙️ Technical Overview & Objectives
This project is an Embedded Python application developed for a Raspberry Pi (Linux environment) that performs real-time data visualization. The core technical achievement is the design and implementation of low-level graphics rendering and a custom algorithm to plot dynamic time-series data onto a small-format, low-resolution ST7789 display.

Key Features and Accomplishments
Custom Cartesian Mapping Algorithm: Developed and implemented a unique linear interpolation algorithm to translate the 12-hour clock state (Hours × Minutes) into precise, custom Cartesian (X, Y) pixel coordinates for real-time plotting.

Low-Level Graphics Rendering: Utilized the Pillow (PIL) library to manually generate all visual elements, including the custom axes, markers, labels, and polygons, demonstrating command over graphics primitives.

High-Speed Hardware Interfacing: Configured the SPI bus at 64MHz for rapid display updates and managed GPIO control for display power and input buttons, ensuring reliable performance in the embedded environment.

Event-Driven Display Logic: Implemented button logic to switch between the real-time graph screen and a static key/title screen.

🛠️ System Requirements & Setup
Hardware
Microprocessor: Raspberry Pi (any model with GPIO header)

Display: Adafruit ST7789-based TFT Display (135x240 or compatible SPI display)

Connectivity: Standard GPIO header wiring for SPI (SCK, MOSI, CE) and dedicated GPIO pins for DC, CS, and Backlight control.

Software Dependencies
The project relies on the following Python packages. These can be installed using the provided requirements.txt file.

Bash

pip3 install -r requirements.txt
Execution
The script requires superuser permissions to access the underlying hardware interfaces (GPIO and SPI).

Bash

sudo python3 chronograph.py
🧠 Algorithm Spotlight: Time Mapping
The central challenge was converting time, which naturally loops (12 hours, 60 minutes), into a linear X, Y coordinate system for plotting on a fixed-size canvas.

The algorithm uses the display's fixed size (plotting_width, plotting_height) to scale the time data:

Time Component	Axis Mapped To	Mapping Logic (Conceptual)
Minute (0-59)	X-Axis (Horizontal)	X_coordinate = LEFT_PADDING + (Current Minute / 59) * Total Plot Width
Hour (1-12)	Y-Axis (Vertical)	Y_coordinate = BOTTOM_PADDING - ((Current Hour - 1) / 11) * Total Plot Height
This conversion allows the system to accurately place the time marker (labeled 'X') on the custom-rendered graph in real-time.
