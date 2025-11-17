## 24h Digital Clock (Design Diagrams)

This repository contains the digital logic design files for a digital clock. The design is captured as a series of block diagrams created in draw.io.

These diagrams illustrate the high-level architecture of the clock's primary counting modules, which form the basis for a hardware implementation (e.g., with logic gates or on an FPGA).

### 📐 Project Components

The system design is broken down into the following modules, each with its own diagram file:

* `Block-Diagram.drawio`: The main, top-level diagram that shows how all the individual modules are interconnected.
* `Pulse Generation Block Diagram .drawio`: The circuit design for the oscillator that generates the clock's time base (e.g., a 1Hz pulse).
* `MOD 60 (Seconds) Block Diagram.drawio`: A modulo-60 counter designed to count from 0 to 59, representing the seconds.
* `MOD 60 (Minutes) Block Diagram.drawio`: A modulo-60 counter, cascaded from the seconds module, to count from 0 to 59 for the minutes.
* `MOD 12 (Hours) Block Diagram.drawio`: A modulo-12 counter, cascaded from the minutes module, to count the hours (e.g., from 1 to 12).

> Note: While the repository is named 24h_digital_clock, the included hour module diagram is for a MOD 12 counter, which is characteristic of a 12-hour clock format.

### 🛠 How to Use

You can open, view, and edit these .drawio files using the [draw.io](https://app.diagrams.net/) website or the official draw.io desktop application.

### 🖼️ Images

![photo_2025-11-17_18-52-13](https://github.com/user-attachments/assets/e275d680-6c28-41b5-ab09-02db99d1e353)

![Uploading photo_2025-11-17_18-52-18.jpg…]()
