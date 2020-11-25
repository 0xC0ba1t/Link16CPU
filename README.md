# Link16CPU
Disclaimer: This processor is currently under development so the code is not available.
<br />
Verilog, Python, Assembly and Makefile 16-bit Multi Core Processor
<br />
This is a multi-core embedded processor. There are a 16 RISC cores, each with a small chunk of local memory and a shared global memory area. Documentation is in the wiki (https://github.com/AdityaCyberSafe/Link16CPU/wiki).
<br />
Required Software
Python 2.7
Icarus Verilog (for simulation) [http://iverilog.icarus.com/]
Altera Quartus (for FPGA)
GNU Make
Assembling Programs
These are in the test directory
<br />
tools/assemble.py tests/sourcefile.hex tests/sourcefile.asm
Replace 'sourcefile' in the command line with the desired file.
<br />
Running in Verilog Simulation
Build the verilog model and bootloader:
<br />
 cd rtl
 make
Run a verilog model making the +bin parameter point to the program you want to run, which should have been assembled already above.
<br />
 vvp multi-sim.vvp +bin=../tests/sourcefile.hex -lxt2
Any value written to address 0xFFFF will be displayed on the console. A trace file will be dumped into 'trace.lxt', which can be read with GTKWave or the like.
<br />
Running on FPGA
This is for the Cyclone II Starter Kit. Synthesize design by opening 'fpga/cIIstarter/cIIstarter.qpf'. Note that the design needs to be resynthesized each time the program is changed.
