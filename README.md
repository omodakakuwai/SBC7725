## SBC7725
The SBC7725 is a home-built single board computer equipped with NEC uPD77P25 DSP, capable of running home-built VTL interpreter.

The SBC7725 has external devices(SRAM,UART) that can be accessed from the DSP.

Since the 7725 DSP does not have Address Bus required for external access, the SBC7725 is designed to output 8-bit high address, 8-bit low address and input/output 8-bit data sequentially on 8bit Data Bus.

the RD# and WR# of the 7725 DSP are input signals from a external host and since these signals cannot be controlled by DSP itself, the SBC7725 uses port output P[1:0] to output status information(it indicates Address output, data output and data input), and the GAL22V10 generates RD# and WR# for the DSP and MRD# and MWR# for external SRAM/UART based on the status information.

A home-built 77P25 ROM writer is used to write VTL interpreter code into the instruction code area(2k words) of internal EPROM.

![](https://github.com/omodakakuwai/SBC7725/blob/main/images/SBC7725.jpg)
![](https://github.com/omodakakuwai/SBC7725/blob/main/images/SBC7725_WRT77P25.jpg)
