## SBC7725
The SBC7725 is a home-built single board computer equipped with NEC uPD77P25 DSP in 80s, capable of running home-built VTL interpreter.

![](https://github.com/omodakakuwai/SBC7725/blob/main/images/SBC7725.jpg)

The SBC7725 has SRAM(32k bytes) and UART(8251) that can be accessed from the DSP.

Since the 7725 DSP does not have Address Bus required for external access, the SBC7725 is designed to output 8-bit high address, 8-bit low address and input/output 8-bit data sequentially on 8bit Data Bus via DR register.

the RD# and WR# of the 7725 DSP are input signals from a external host and since these signals cannot be controlled by DSP itself, the SBC7725 uses port output P[1:0] to output status information (it indicates address output, data output and data input), and the GAL22V10 generates RD# and WR# for the DSP and MRD# and MWR# for SRAM/UART based on the status information.

A home-built 77P25 ROM writer (WRT77P25) is used to write VTL interpreter code into the instruction code area (2k words) of internal EPROM.

![](https://github.com/omodakakuwai/SBC7725/blob/main/images/SBC7725_WRT77P25.jpg)

The SBC7725 is developed using a universal board and is planned to be developed using a printed circuit board.
