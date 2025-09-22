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

 <img width="575" alt="yosys" src="https://github.com/harshkanoje/VSD_RISC_Program/img1.png">


</details>
