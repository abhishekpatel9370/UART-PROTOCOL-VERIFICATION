# UART Protocol Verification – Self-Checking Testbench

## Project Overview
In this project, I verified a **UART (Universal Asynchronous Receiver-Transmitter) protocol** design using a **self-checking SystemVerilog testbench**.  
The verification environment is fully automated — it generates stimulus, drives the DUT, monitors outputs, and compares results without manual intervention.

The DUT (`uart_top`) implements UART transmission and reception, and the testbench ensures that:
- Data transmitted is correctly received.
- Protocol timing and control signals are followed.
- The design works for both **write** and **read** operations.

---

## Key Features
- **Self-checking mechanism** using a scoreboard to compare expected and actual data.
- **Class-based testbench architecture** with:
  - **Generator** – Creates randomized UART transactions.
  - **Driver** – Applies stimulus to DUT via a virtual interface.
  - **Monitor** – Observes DUT behavior without driving it.
  - **Scoreboard** – Checks data integrity and reports PASS/FAIL.
  - **Environment** – Connects and manages all components.
- **Randomized testing** for better coverage.
- Supports both **TX (transmit)** and **RX (receive)** operations.
- **Event and mailbox-based synchronization**.
- **Waveform dump** for visual debugging.

---

## How It Works
1. **Generator** creates randomized UART operations (`read` or `write`).
2. **Driver** sends/receives data to/from the DUT according to the operation type.
3. **Monitor** captures DUT signals and reconstructs the transmitted/received data.
4. **Scoreboard** compares monitored data with the expected data from the driver.
5. Test continues until the configured number of transactions is completed.


