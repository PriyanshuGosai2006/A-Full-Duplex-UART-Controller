# SystemVerilog Full-Duplex UART

## Overview
A synthesizable, full-duplex Universal Asynchronous Receiver-Transmitter (UART) IP core written in SystemVerilog. The design uses 16x oversampling and double-flop metastability synchronization to reliably sample asynchronous serial data into a 100 MHz synchronous clock domain.
* Schematic :
 <img width="1918" height="901" alt="image" src="https://github.com/user-attachments/assets/5c1db4ea-5f1d-40ac-9a84-e7fecbe87d4e" />


## Technical Specifications
* **Protocol:** 8-N-1 (8 Data Bits, No Parity, 1 Stop Bit)
* **Baud Rate:** Parameterized (Default: 9600 bps)
* **Clocking:** Single 100 MHz clock domain (cycle-accurate, zero gated clocks)
* **Design Pattern:** Interface-based architecture (`uart_if.sv`) to cleanly abstract hardware data buses.
  

## Verification
Verified via a self-checking testbench in ModelSim/Questa. The testbench drives a physical loopback (TX tied to RX) to validate simultaneous full-duplex transmission and reception.

<img width="1290" height="552" alt="waveform" src="https://github.com/user-attachments/assets/1712d559-5b83-420e-b4b0-adbf087f43be" />
<img width="725" height="157" alt="image" src="https://github.com/user-attachments/assets/d652a417-2c6a-4c32-b7e5-cfce264105a1" />



## Synthesis & Timing
Synthesized using AMD Vivado targeting the Xilinx Artix-7 (`xc7a35tcpg236-1`). 

* **Clock Constraint:** 100 MHz (10.000 ns period)
* **Setup/Hold Violations:** None
* **Worst Negative Slack (WNS):** +5.962 ns
* Slice LUTS : 60
* Slice Registers : 59
* Synthesis & Resource Utilization (Flattened post-synthesis schematic proving physical translation to Artix-7 LUTs and Registers):
 <img width="1910" height="392" alt="image" src="https://github.com/user-attachments/assets/d6232de3-fb2b-4c4a-9866-a1e565f4a8bf" />


  

<img width="1032" height="261" alt="timing&#39;" src="https://github.com/user-attachments/assets/32fe623f-0da1-4f5f-a44c-03451b3c6892" />

