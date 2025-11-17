## Digital Clock (Without Microcontrollers)

[cite_start]This project is a final report for the EEE14357 Digital Systems Design Lab at Palestine Technical College - Deir Al Balah[cite: 1, 2, 4].

[cite_start]The project, completed in June 2023, is the design and implementation of a 24-hour digital clock that displays seconds, minutes, and hours[cite: 13, 19]. [cite_start]The primary constraint and focus of the project was to achieve this functionality using discrete digital logic integrated circuits (ICs), with **no microcontrollers**[cite: 6, 16, 17].

[cite_start]The clock also features two push-buttons to manually adjust the minutes and hours[cite: 20].
  
### 🖼️ Images

![photo_2025-11-17_18-52-13](https://github.com/user-attachments/assets/e275d680-6c28-41b5-ab09-02db99d1e353)
![photo_2025-11-17_18-52-18](https://github.com/user-attachments/assets/d23be02a-c089-4e4d-a5bf-3a74bd32d64d)

### ⚙️ How It Works

[cite_start]The circuit is comprised of three main stages: Seconds, Minutes, and Hours[cite: 155]. The logic flows from one stage to the next.

#### 1. Pulse Generation (Time Base)
[cite_start]The heart of the clock is an **NE555P Timer IC** (U1)[cite: 65]. [cite_start]It is configured as an astable multivibrator to generate a continuous, stable clock pulse[cite: 151]. [cite_start]The circuit is designed with resistors and capacitors to produce a frequency of approximately **1.085 Hz**, which acts as the 1-second "tick" that drives the entire clock[cite: 147].

#### 2. Counting & Display (Cascaded Stages)
[cite_start]The project uses six **CD4026BE ICs** (U2-U7)[cite: 24]. [cite_start]This chip is ideal for this project as it functions as both a decade counter (counts 0-9) and a 7-segment display driver in one package[cite: 23].

* [cite_start]Each 4026 IC is connected to one 7-segment display to show a single digit[cite: 151].
* [cite_start]The counters are **cascaded** by connecting the **Carry Out (pin 5)** of one counter to the **Clock (pin 1)** of the next[cite: 159, 160].
* [cite_start]This way, when the "seconds-units" counter (U2) rolls over from 9 to 0, it sends a single pulse to the "seconds-tens" counter (U3), incrementing it by one[cite: 161]. This pattern repeats for the minutes and hours stages.

#### 3. Reset Logic (Modulo Counting)
Since the CD4026BE counts to 9, an external logic circuit is needed to reset the stages at the correct times (e.g., 60 seconds, 60 minutes, 24 hours). [cite_start]This is accomplished using an **SN74LS11N IC**, which contains triple 3-input AND gates[cite: 85, 88].

* **MOD-60 (Seconds & Minutes):** The seconds stage (U2, U3) and minutes stage (U4, U5) must reset after 59. An AND gate monitors the outputs of the "tens" digit counter (U3 and U5). [cite_start]When this counter attempts to display a "6", the AND gate detects it and sends a HIGH signal to the **RESET (pin 15)** of both ICs in that stage, forcing them back to 00[cite: 162, 166, 173].
* [cite_start]**MOD-24 (Hours):** A similar logic resets the hours stage (U6, U7)[cite: 168]. An AND gate (U9A) monitors the outputs of both hour counters. [cite_start]When the display tries to show "24", the gate sends a reset pulse to U6 and U7, forcing them back to 00[cite: 170, 176].

#### 4. Power Supply
[cite_start]The circuit is powered by an **L7805CV** linear voltage regulator, which takes a higher input voltage and provides a stable 5V output required by the ICs[cite: 106, 110, 111].

### 📋 Main Components

* [cite_start]**1x NE555P** (Timer IC) [cite: 66]
* [cite_start]**6x CD4026BE** (Decade Counter / 7-Segment Driver) [cite: 24]
* [cite_start]**6x 5161AS** (7-Segment Display, Common Cathode) [cite: 61, 62]
* [cite_start]**1x SN74LS11N** (Triple 3-Input AND Gate) [cite: 88]
* [cite_start]**1x L7805CV** (5V Voltage Regulator) [cite: 112]
* [cite_start]**2x Push Buttons** (for setting time) [cite: 20]
* **2x Diodes** (for isolating set buttons)
* [cite_start]Various resistors and capacitors for timing and current limiting [cite: 147]



