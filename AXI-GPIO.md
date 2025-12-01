# **What is AXI GPIO?**

The AXI GPIO is a 32-bit general-purpose I/O IP core that interfaces with the AXI4-Lite bus.  
It allows the processor to **read or write FPGA pins** through memory-mapped registers.

---

# **1. Internal Architecture**

AXI GPIO has 3 main parts:

## **(a) AXI4-Lite Interface**
Provides register access from the processor:
- `GPIO_DATA` – pin values
- `GPIO_TRI` – direction (1=input, 0=output)
- `GPIO2_DATA` – second channel data
- `GPIO2_TRI` – second channel direction

## **(b) GPIO Channels**
- Channel 1 (GPIO) — mandatory  
- Channel 2 (GPIO2) — optional  
Each can act as:
- Input  
- Output  
- Bidirectional (via software direction control)

## **(c) Optional Interrupts**
Input changes can trigger interrupts.

---

# **2. AXI GPIO in Vivado (Direction Settings)**

Vivado provides **All Inputs** and **All Outputs** checkboxes for each channel:

### **All Inputs**
- Entire channel is fixed as input  
- CPU only reads values  
- Used for: buttons, switches, sensors

### **All Outputs**
- Entire channel is fixed as output  
- CPU writes to drive signals  
- Used for: LEDs, displays, digital control lines

### **Mixed Direction (Software-Controlled)**
- Leave **both** checkboxes unchecked  
- Direction is set per bit using `GPIO_TRI`  
- Useful when a channel must contain both input and output pins

---

# **3. How AXI GPIO Works With Zynq**

1. Zynq PS ↔ AXI Interconnect ↔ AXI GPIO  
2. AXI GPIO ↔ FPGA pins or custom logic  
3. ARM processor accesses GPIO through AXI4-Lite registers for reading/writing pins
