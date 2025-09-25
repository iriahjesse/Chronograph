# ChronoGraph: Embedded Linux Visualization System

Embedded Python visualization system featuring a custom time-to-coordinate mapping algorithm for a constrained SPI display.

---

## ⚙️ Technical Overview & Objectives

This project is an **Embedded Python** application developed for a Raspberry Pi (Linux environment) that performs real-time data visualization. The core technical achievement is the design and implementation of low-level graphics rendering and a custom algorithm to plot dynamic time-series data onto a small-format, low-resolution ST7789 display.

### Key Features and Accomplishments

* **Custom Cartesian Mapping Algorithm:** Developed and implemented a unique **linear interpolation algorithm** to translate the 12-hour clock state (Hours $\times$ Minutes) into precise, custom **Cartesian (X, Y) pixel coordinates** for real-time plotting.
* **Low-Level Graphics Rendering:** Utilized the **Pillow (PIL) library** to manually generate all visual elements, including the custom axes, markers, labels, and polygons, demonstrating command over graphics primitives.
* **High-Speed Hardware Interfacing:** Configured the **SPI bus at 64MHz** for rapid display updates and managed GPIO control for display power and input buttons, ensuring reliable performance in the embedded environment.
* **Event-Driven Display Logic:** Implemented button logic to switch between the real-time graph screen and a static key/title screen.

---

## 🛠️ System Requirements & Setup

### Hardware

* **Microprocessor:** Raspberry Pi (any model with GPIO header)
* **Display:** Adafruit ST7789-based TFT Display (135x240 or compatible SPI display)
* **Connectivity:** Standard GPIO header wiring for SPI (SCK, MOSI, CE) and dedicated GPIO pins for DC, CS, and Backlight control.

### Software Dependencies

The project relies on the following Python packages. These can be installed using the provided `requirements.txt` file.

```bash
pip3 install -r requirements.txt
