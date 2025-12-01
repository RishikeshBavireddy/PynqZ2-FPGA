
# **What is AXI GPIO?**

The AXI GPIO provides a general purpose input/output interface to the AXI (Advanced eXtensible Interface) interface. This 32-bit soft IP core is designed to interface with the AXI4-Lite interface.

You use it when you want the processor on the FPGA board to **read or write FPGA pins**.

---

# **1. Internal Architecture**

AXI GPIO has 3 main parts:

## **(a) AXI4-Lite Interface**
- Allows the processor to access registers inside the GPIO IP  
- Typical registers:  
  - `GPIO_DATA` – read/write pin values  
  - `GPIO_TRI` – sets **direction** (1=input, 0=output)  
  - `GPIO2_DATA` – second channel  
  - `GPIO2_TRI` – second channel direction  

## **(b) GPIO Channels**
- **Channel 1 (GPIO)** — mandatory  
- **Channel 2 (GPIO2)** — optional  
- Each channel can be:  
  - Input  
  - Output  
  - Bidirectional  

## **(c) Optional Interrupts**
- GPIO can generate interrupts when input pins change state  

---

# **2. AXI GPIO in Vivado **


---

# **3. How AXI GPIO Works With Zynq**

Typical connections:
1. Zynq PS → AXI Interconnect → AXI GPIO  
2. AXI GPIO → FPGA pins or custom HDL  
3. ARM CPU reads/writes the GPIO over AXI4-Lite registers  
