MIPS-Verilog
============

mips r3000 processor verilog code to be synthesized on Spartan 3E FPGA.

<h3>This project consists of 4 Parts :</h3>
<ul>
  <li>Single Cycle Processor</li>
  <li>Multi Cycle Pipelined Processor (Without Forwarding)</li>
  <li>Hazard Free Multi Cycle Processor (With Forwarding)</li>
  <li>.coe TestCases</li>
</ul>

In order to run this project, you might need to regenerate memories for Instruction and Data Memory using IPCore in Xilinx. You can then load the coe files in your Instruction memory.

<h3>Single Cycle Processor</h3>
This part lacks unaligned load in memory and lh sh instructions.
<h3>Multi Cycle Processor</h3>
This part lacks jump instructions and lh, sh and unaligned load.
<h3>Multi Cycle with Forwarding Processor</h3>
This part lacks jump instructions and lh, sh and unaligned load.

<h3>Core.v</h3>
This file consists of the main parts of our processor. Instruction Fetch is done using the generated Instruction Memory. 
Instruction Decode is done using an always loop, Control Unit is also implemented as an always block, ALU has another always block on it's own.
The forwarding multiplexers and forwarding unit has another always block.

<h3>Core_TB.v</h3>
This file is our testbench, it instantiates Core.v and generates clock and nrst signal in order for our Core module to work. You can then monitor the processor's behavior using either ISim or Modelsim.
<h3>reg_bank.v</h3>
This module is our register bank which reads asynchronously and writes on negative clk edge. We have modified our register banks to read on the clk edge for our pipelined versions.
<h3>IMem.v</h3>
This module is generated by IPCore Generator and is our Instruction memory. (Size: 32x64)
<h3>DMem.v</h3>
This module is generated by IPCore Generator and is our Data memory. We instantiate it four times in our Core module. (Size: 8x64)
<h3>*.coe</h3>
These are our instructions that will be loaded in Instruction Memory to be executed.
