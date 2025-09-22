<details>

<summary>	
 Day - 0  Tools Installation
</summary>

## Yosys

- Purpose: Open-source framework for RTL synthesis (mainly Verilog).

```
$ yosys -V
```
ouput :

```

 /----------------------------------------------------------------------------\
 |  yosys -- Yosys Open SYnthesis Suite                                       |
 |  Copyright (C) 2012 - 2025  Claire Xenia Wolf <claire@yosyshq.com>         |
 |  Distributed under an ISC-like license, type "license" to see terms        |
 \----------------------------------------------------------------------------/
 Yosys 0.57+153 (git sha1 d60dc93e9, g++ 13.3.0-6ubuntu2~24.04 -fPIC -O3)


```
## Iverilog

Purpose: Simulator for Verilog HDL.

```
$ sudo apt-get install iverilog
$ iverilog -V
```
ouput :

```Icarus Verilog version 12.0 (stable) ()

Copyright (c) 2000-2021 Stephen Williams (steve@icarus.com)

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 2 of the License, or
  (at your option) any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU General Public License along
  with this program; if not, write to the Free Software Foundation, Inc.,
  51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

Icarus Verilog Preprocessor version 12.0 (stable) ()

Copyright (c) 1999-2021 Stephen Williams (steve@icarus.com)

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 2 of the License, or
  (at your option) any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU General Public License along
  with this program; if not, write to the Free Software Foundation, Inc.,
  51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

Icarus Verilog Parser/Elaborator version 12.0 (stable) ()

Copyright (c) 1998-2021 Stephen Williams (steve@icarus.com)

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 2 of the License, or
  (at your option) any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU General Public License along
  with this program; if not, write to the Free Software Foundation, Inc.,
  51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

 FLAGS DLL vvp.tgt
vvp.tgt: Icarus Verilog VVP Code Generator 12.0 (stable) ()

Copyright (c) 2001-2021 Stephen Williams (steve@icarus.com)

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 2 of the License, or
  (at your option) any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU General Public License along
  with this program; if not, write to the Free Software Foundation, Inc.,
  51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.


```

## GTKWave

purpose : to check waveforms and visualize vcd file 

```
$ sudo apt update
$ sudo apt install gtkwave
$ gtkwave -V
```
ouput :

```
GTKWave Analyzer v3.3.116 (w)1999-2023 BSI

This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```
</details>


<details>
	<summary>Day - 1 Intro to Verilog RTL and Sysnthesis</summary>

 ## Basics
 Understanding Simulator an cmd terimnal prompts
 
 Simulator--> Making framework adhering to required specs
 Testbenched --> to apply stimulus to design to check its functionality

from both these, we obtain a VCD file which can be visulaized using GTK Wave
<Img>

 
 Synthesizer --> Tool for converting RTL to Netlist

# Workflow Steps
## 1. RTL Synthesis

Input: RTL (typically Verilog) source code is provided as the starting point for digital logic design.
Tool: Yosys performs synthesis to generate a gate-level netlist—essentially a mapping from RTL logic to basic gates

 <img width="575" alt="yosys" src="https://github.com/harshkanoje/VSD_RISC_Program/blob/main/Images/im1">

 .lib liberty file specifically as libsky130fdschdtt025C1v80.lib, which is used in the technology mapping stage of the RTL to physical design flow. This file allows synthesis and mapping tools such as Yosys and abc cmd to assign synthesized logic to actual physical library cells present in the Skywater SKY130 PDK

## Mapping netlist according process design kit avail for Sky130 nm
 
Mapping: The netlist is processed using the ABC tool, which maps gates to specific cells from the SKY130 standard cell library (libsky130fdschdtt025C1v80.lib).

Results: Output lists detailed cell types, input and output signal counts for each mapped functional block (e.g., muxes, logic gates).

```
Yosys > abc -liberty lib/sky130_fd_sc_hd__tt_025C_1v80.lib

```

This command explicitly links the synthesis process to the **`sky130_fd_sc_hd`** cell library 

Following the re-integration of the ABC results (Section 4.1.2) [1], the synthesized netlist was optimized down to a minimal structure .
```

| Metric | Result | Source |
| :--- | :--- | :--- |
| **Total Cells Used** | 1 | [1] |
| **Specific Cell Type** | `sky130_fd_sc_hd__mux2_1` | [1] |
| **Input Signals** | 3 | [1] |
| **Output Signals** | 1 | [1] |
| **Internal Signals** | 0 | [1] |
```
This confirms the circuit maps entirely onto a single **2-to-1 multiplexer** standard cell.

## Post-Synthesis Steps

Once optimization and technology mapping were complete, temporary directories associated with the ABC synthesis were removed .

Final verification involved issuing the `Yosys > show` command, which is used to generate a visual representation of the resulting netlist 

 <img width="575" alt="yosys" src="https://github.com/harshkanoje/VSD_RISC_Program/blob/main/Images/im4.png">

## 5. Visual Documentation 

To fully document the project, the following images should be generated from the tools and included in the Markdown file:

### 5.1. High-Level Design Flow Diagram
This image should illustrate the high-level progression, visually representing the sequence: **RTL → Yosys → netlist → PDK → physical design → fab**. This provides context for the tool chain.

### 5.2. Synthesized Netlist Visualization
This image is the direct output of the `Yosys > show` command [1]. It must visually confirm the minimal complexity of the final design, showing:
*   **One** primary cell: the **`sky130_fd_sc_hd__mux2_1`**.
*   The connections demonstrating the **3 input signals** and **1 output signal** .

### 5.3. Standard Cell Context (Recommended)
A schematic or layout view of the **`sky130_fd_sc_hd__mux2_1`** cell included to provide technological depth regarding the physical implementation of the logic .

 <img width="575" alt="yosys" src="https://github.com/harshkanoje/VSD_RISC_Program/blob/main/Images/im6.png">




</details>
