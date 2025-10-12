## SBC7725
The SBC7725 is a home-built single board computer equipped with NEC uPD77P25 DSP in 80s, capable of running home-built VTL interpreter.

The SBC7725 has external devices (32k bytes SRAM, 8251 UART) that can be accessed from the DSP.

Since the 7725 DSP does not have Address Bus required for external access, the SBC7725 is designed to output 8-bit high address, 8-bit low address and input/output 8-bit data sequentially on 8bit Data Bus.

the RD# and WR# of the 7725 DSP are input signals from a external host and since these signals cannot be controlled by DSP itself, the SBC7725 uses port output P[1:0] to output status information (it indicates Address output, data output and data input), and the GAL22V10 generates RD# and WR# for the DSP and MRD# and MWR# for external SRAM/UART based on the status information.

A home-built 77P25 ROM writer (WRT77P25) is used to write VTL interpreter code into the instruction code area (2k words) of internal EPROM.

The SBC7725 was developed using a universal board and is planned to be developed using a printed circuit board.

VTL interpreter is also implemented based on several ideas. 

The first idea is the realization of call nesting. 
Since the four-level HW stack in the DSP is insufficient to perform recursive processing using call nesting, VTL implements a SW stack. 
When a pseudo-call is called, a label value indicating the pseudo-call number is PUSHed onto the SW stack and when a pseudo-return is executed, the label value is POPed from the SW stack. 
These implementaions make call nesting possible. 

The second idea is to identify the JMP destination in a psedo-return. 
Since the DSP only have an immediate-value JMP instruction, it cannot execute indirect JMP using the label value.
Therefore, a binary tree search is performed based on the label value to find the corresponding JMP instruciton from a pre-defined set of immediate-value JMP insturions.

![](https://github.com/omodakakuwai/SBC7725/blob/main/images/SBC7725.jpg)
![](https://github.com/omodakakuwai/SBC7725/blob/main/images/SBC7725_WRT77P25.jpg)
