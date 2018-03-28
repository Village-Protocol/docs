ZeBu<sup>®</sup> Server

Release Notes

**Patch** **K-2015.09-6 **

November 2016

**Copyright Notice and  
Proprietary Information**

© 2016 Synopsys, Inc. All rights reserved. This Synopsys software and
all associated documentation are proprietary to Synopsys, Inc. and may
only be used pursuant to the terms and conditions of a written license
agreement with Synopsys, Inc. All other use, reproduction, modification,
or distribution of the Synopsys software or the associated documentation
is strictly prohibited.

**Destination Control Statement**

All technical data contained in this publication is subject to the
export control laws of the United States of America. Disclosure to
nationals of other countries contrary to United States law is
prohibited. It is the reader's responsibility to determine the
applicable regulations and to comply with them.

**Disclaimer**

SYNOPSYS, INC., AND ITS LICENSORS MAKE NO WARRANTY OF ANY KIND, EXPRESS
OR IMPLIED, WITH REGARD TO THIS MATERIAL, INCLUDING, BUT NOT LIMITED TO,
THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
PURPOSE.

**Trademarks**

Synopsys and certain Synopsys product names are trademarks of Synopsys,
as set forth at <http://www.synopsys.com/Company/Pages/Trademarks.aspx>.

All other product or company names may be trademarks of their respective
owners.

**Third-Party Links**

Any links to third-party websites included in this document are for your
convenience only. Synopsys does not endorse and is not responsible for
such websites and their practices, including privacy practices,
availability, and content.

Synopsys, Inc.

690 E. Middlefield Road

Mountain View, CA 94043

[www.synopsys.com](http://www.synopsys.com)

# Table of Contents

About This Document 4

1 Prerequisites 5

1.1 General Requirements 5

1.2 Xilinx Place & Route Tools 5

1.3 Synopsys Interoperable Technologies 5

1.4 Regenerating the Setup Directory ($ZEBU\_SYSTEM\_DIR) 5

2 New Behaviors and Changes 6

2.1 Usage of Verilog delays and Clock Tolerance (STAR \#9001028172) 6

2.2 Updates to zSpy Option (STAR \#9001033958) 6

2.3 Unified Compile Command Updates 6

2.3.1 Modified Commands/Options 6

2.3.2 New Commands/Options 7

3 Fixes and Enhancements 10

3.1 Synthesis 10

3.2 Elaboration with VCS 10

3.3 zCui 11

3.4 Back-End Compilation 11

3.5 Power-Aware Verification 12

3.6 Emulation Runtime 12

3.7 Post-Run Debugging 13

4 Documentation Updates 14

# About This Document

This Release Notes provide information on limitations, known issues,
fixes, and enhancements for ZeBu patch K-2015.09-6.

It is intended for ZeBu Server-1, ZeBu Server-2, ZeBu Blade-2, and ZeBu
Server-3.

This document is intended for users who are familiar with the ZeBu
product range.

# Prerequisites

This section provides a list of prerequisites that are required for
installing the K-2015.09-6 patch.

## General Requirements

  - This patch requires users to recompile the design and testbenches
    before proceeding with the emulation runtime.

  - This patch requires users to re-run emulation before using **CSA**
    or **zPostRunDebug**.

## Xilinx Place & Route Tools

The following table provides information about the Xilinx Place & Route
tools that are tested with the present version of the ZeBu
software.

| Xilinx Place & Route Tool                        | Tested Versions | Version Limit |
| ------------------------------------------------ | --------------- | ------------- |
| ISE Place & Route (ZeBu Server-1, ZeBu Server-2) | 13.4\_patched   | 2012.01       |
| Vivado Place & Route (ZeBu Server-3)             | 2015.1          | 2015.04       |
| Triton Place & Route (ZeBu Server-3)             | 2014.1-sp29     | N/A           |

## Synopsys Interoperable Technologies

The following table provides information about the Synopsys
interoperable technologies that are tested with the present version of
the ZeBu software.

| Synopsys Tool     | Tested Version  |
| ----------------- | --------------- |
| VCS MX            | K-2015.09-SP2-7 |
| Verdi<sup>3</sup> | K-2015.09-SP2-7 |
| DesignWare BB     | K-2015.06       |

## Regenerating the Setup Directory ($ZEBU\_SYSTEM\_DIR)

1.  To regenerate the setup directory, you must always use zSetupSystem
    and zUtils -initSystem from the latest ZeBu release.

# New Behaviors and Changes

This section provides a list of new behaviors and changes and explains
them in detail.

This section contains the following sub-section(s).

  - Usage of Verilog delays and Clock Tolerance (STAR \#9001028172)

  - Updates to zSpy Option (STAR \#9001033958)

  - Unified Compile Command Updates

## Usage of Verilog delays and Clock Tolerance (STAR \#9001028172)

With K-2015.09-6 patch release, clock tolerance and Verilog delays can
be used at the same time.

## Updates to zSpy Option (STAR \#9001033958)

With K-2015.09-6 patch release, zSpy -status displays for each module,
whether the module is used or free.

If the module is used, a list of displayed fields provide more
information about the run that uses the module. The list of fields is
customizable.

For more information, see zSpy –help.

## Unified Compile Command Updates

This section provides information about deprecated and new UTF commands.

1.  1.  With K-2015.09-6 release and future releases, the “clock\_config
        -accuracy=32” command is not accepted; instead the
        “clock\_config -accuracy 32” command is accepted.
    
    2.  Some shortcut names that worked in previous releases, like
        “timing” instead of “timing\_analysis” are not unique, and no
        longer work. In future releases, any kind of short cuts are not
        allowed anymore. For further assistance, contact Synopsys
        support.

This section contains the following sub-section(s).

  - Modified Commands/Options

  - New Commands/Options

### Modified Commands/Options

With the K-2015.09-6 patch release, the following commands are modified.

  - Updates to wire\_resolution Commands (STAR \# 9001089939)

  - Updates to Synthesis Commands

  - Additional zmem\_clock\_frequency Values for memory\_preferences
    Command (STAR \#9001088236)

#### Updates to wire\_resolution Commands (STAR \# 9001089939)

With the K-2015.09-6 patch release, the wire\_resolution command is
replaced with the following commands.

wire\_resolution \[-conflict WAND|WOR\] \[-wires \<list\>\]

wire\_resolution \[-default\_conflict WOR|WAND\] \[-default\_undriven
0|1\] \[-default\_tristate PULLUP|PULLDOWN|KEEPER\]

#### Updates to Synthesis Commands (STAR \# 9001072622)

With the K-2015.09-6 patch release, the following synthesis command that
includes synthesis -debug command is replaced with the following
commands:

synthesis -debug\_fmcheck\_dump\_only \<bool\>

synthesis -debug\_fmcheck\_dump
\<bool\>

#### Additional zmem\_clock\_frequency Values for memory\_preferences Command (STAR \#9001088236)

With K-2015.09-6 patch release, additional zmem\_clock\_frequency values
are included in memory\_preferences -zmem\_clock\_frequency command:

  - 25

  - 50

  - 100

  - 200

  - AUTO (obtains default value)

### New Commands/Options

With the K-2015.09-6 patch release, the following new commands are
added.

  - clock\_config -number\_of\_bufgs \<int\> Command (STAR \#
    9001091940)

  - clustering -auto\_block\_selection Command (STAR \# 9001094368)

  - clustering -netlist\_file\_mode GZFILE|GZSTREAM|STREAM Command

  - cluster\_constraint -command \<cmd\> \<args\> Command

  - timing\_constraint -command SET\_FALSE\_PATH \<args\> Command

  - design -drive\_strength\_support \<bool\> Command (STAR
    \#9001082031)

  - timing\_analysis -delay\_min\_zfilter\_skew \<int\> Command (STAR \#
    9001097778)

  - timing\_analysis -advanced\_async\_set\_reset\_analysis \<bool\>
    Command (STAR \# 9001097777)

  - timing\_analysis -use\_hdl\_names \<bool\> Command (STAR \#
    9001090983)

  - dpi\_synthesis -frequency \<int\> Command (STAR \#9001060976)

  - clocks -clear\_internal\_clk\_data \<bool\>
Command

#### clock\_config -number\_of\_bufgs \<int\> Command (STAR \# 9001091940)

With K-2015.09-6 patch release, a new UTF option is introduced for the
existing clock\_config to set the number of BUFGs available for DUT
clock routing in the FPGAs.

clock\_config -number\_of\_bufgs \<int\>

#### clustering -auto\_block\_selection Command (STAR \# 9001094368)

With K-2015.09-6 patch release, a new UTF option is introduced for the
clustering -auto\_block\_selection command to enable/disable ABS mode.

clustering -auto\_block\_selection \<bool\>

<table>
<thead>
<tr class="header">
<th>Clustering Command Value</th>
<th>Status of ABS Mode</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>clustering -auto_block_selection true</td>
<td><p>Enables ABS mode.</p>
<p>Maps to the partitioning auto -auto_block_selection command</p></td>
</tr>
<tr class="even">
<td>clustering -auto_block_selection false</td>
<td>Disables ABS mode</td>
</tr>
</tbody>
</table>

#### clustering -netlist\_file\_mode GZFILE|GZSTREAM|STREAM Command

With K-2015.09-6 patch release, a new UTF option, clustering
-netlist\_file\_mode GZFILE|GZSTREAM|STREAM, is introduced to specify
modes for passing netlist data from **zTopBuild** to **zTopClustering**.

  - GZFILE is for gzipped netlist file (default)

  - GZSTREAM is for gzipped netlist file through a pipe

  - STREAM drives netlist file through a pipe from **zTopBuild** to
    **zTopClustering**

#### cluster\_constraint -command \<cmd\> \<args\> Command

With K-2015.09-6 patch release, a new UTF option, cluster\_constraint
-command \<cmd\> \<args\>, is introduced to apply

  - partitioning constraints at Core and FPGA levels through several
    commands, and

  - defining cores, groups of instances, and merging blocks.

#### timing\_constraint -command SET\_FALSE\_PATH \<args\> Command

With K-2015.09-6 patch release, a new UTF option, timing\_constraint
-command SET\_FALSE\_PATH \<args\>, is introduced to specify false path
constraints to or from port/instance/alias
names.

#### design -drive\_strength\_support \<bool\> Command (STAR \#9001082031)

The design -drive\_strength\_support \<bool\> command is used to
enable/disable drive\_strength\_support mode (resolves
undriven/multidriven/tristate signals using drive strength semantics)
using the following:

design -drive\_strength\_support
\<bool\>

#### timing\_analysis -delay\_min\_zfilter\_skew \<int\> Command (STAR \# 9001097778)

With K-2015.09-6 patch release, a new UTF option is introduced for the
timing\_analysis command to set the minimum delay (in \[ps\]) between
filter to skew (Default: 40000) using the following:

timing\_analysis -delay\_min\_zfilter\_skew \<int\>

This command replaces the following **zTime** command.

set\_eval\_param
DELAY\_MIN\_ZFILTER\_SKEW=\<int\>

#### timing\_analysis -advanced\_async\_set\_reset\_analysis \<bool\> Command (STAR \# 9001097777)

With K-2015.09-6 patch release, a new UTF option is introduced for the
timing\_analysis command to enable/disable
advanced\_asynchronous\_set\_reset\_analysis mode (adds asynchronous
path into account at multi-cycle path analysis) using the following:

timing\_analysis -advanced\_async\_set\_reset\_analysis \<bool\>

If the argument is set to “true,” this command replaces the previous
zTime command: set\_advanced\_asynchronous\_set\_reset\_analysis
true

#### timing\_analysis -use\_hdl\_names \<bool\> Command (STAR \# 9001090983)

With K-2015.09-6 patch release, a new UTF option is introduced for the
existing timing\_analysis command:

timing\_analysis -use\_hdl\_names \<bool\>

When the argumentis set to “true” the original names are used by the
timing reports.

#### dpi\_synthesis -frequency \<int\> Command (STAR \#9001060976)

With the K-2015.09-6 patch release, a new option is introduced for
dpi\_synthesis command to specify the theoretical DPI frequency (in KHz)
to be reached at run-time.

dpi\_synthesis -frequency
\<int\>

#### clocks -clear\_internal\_clk\_data \<bool\> Command (STAR \# 9000966833)

With K-2015.09-6 patch release, a new UTF option is introduced, clocks
-clear\_internal\_clk\_data \<bool\>, to clear all paths that were
previously specified using -add\_internal\_clk and -add\_internal\_data
options.

# Fixes and Enhancements

This section provides a list of STARs fixed with this patch in ZeBu
compilation flow order.

## Synthesis

| STAR\#     |
| ---------- |
| 9001070215 |
| 9001070220 |
| 9001071258 |
| 9001016408 |
| 9001043528 |
| 9001049991 |
| 9001063831 |
| 9001069901 |
| 9001072713 |
| 9001076636 |
| 9001077015 |
| 9001078692 |
| 9001081248 |
| 9001082861 |
| 9001082923 |
| 9001088869 |
| 9001093820 |
| 9001094455 |

## Elaboration with VCS

| STAR\#     |
| ---------- |
| 9000933194 |
| 9000964182 |
| 9000988305 |
| 9001012409 |
| 9001028734 |
|            |
| 9001039756 |
| 9001041709 |
| 9001059539 |
| 9001065659 |
| 9001066700 |
| 9001067590 |
| 9001067853 |
| 9001068735 |
| 9001070246 |
| 9001073260 |
| 9001074248 |
| 9001074342 |
| 9001077499 |
| 9001079676 |
| 9001082501 |
| 9001083441 |
| 9001085203 |
| 9001087333 |
| 9001087335 |
| 9001087404 |
| 9001093323 |
| 9001093364 |
| 9001097050 |
| 9001097607 |
| 9001100479 |

## zCui

| STAR\#     |
| ---------- |
| 9001043343 |
| 9001080811 |
| 9001092204 |
| 9001094807 |

## Back-End Compilation

| STAR\#     |
| ---------- |
| 9000984547 |
| 9001006444 |
| 9001025992 |
| 9001039653 |
| 9001060062 |
| 9001061971 |
| 9001063689 |
|            |
| 9001066163 |
| 9001072043 |
| 9001072521 |
| 9001076445 |
| 9001080255 |
| 9001080337 |
| 9001080604 |
| 9001082756 |
| 9001083520 |
| 9001086258 |
| 9001089950 |
| 9001091234 |
| 9001091954 |
| 9001098371 |
| 9001102018 |
| 9001110133 |
| 9001111219 |
| 9001112997 |
| 9001094849 |
| 9001102425 |
| 9001113368 |

## Power-Aware Verification

| STAR\#     |
| ---------- |
| 9000962893 |
| 9000979188 |
| 9001053010 |
| 9001071633 |
| 9001072482 |
| 9001073861 |
| 9001074575 |
| 9001074925 |
| 9001076405 |
| 9001077801 |
| 9001083430 |
| 9001085367 |
| 9001086143 |
| 9001087826 |
| 9001095212 |
| 9001095596 |
| 9001084131 |

## Emulation Runtime

| STAR\#     |
| ---------- |
| 9001027074 |
| 9001028172 |
| 9001059788 |
| 9001060344 |
| 9001062432 |
| 9001066374 |
| 9001067563 |
| 9001067613 |
| 9001077666 |
| 9001081255 |
| 9001083690 |
| 9001084691 |
| 9001085112 |
| 9001086818 |
| 9001089447 |
| 9001090418 |
| 9001100791 |
| 9001113420 |

## Post-Run Debugging

| STAR\#     |
| ---------- |
| 9001021274 |
| 9001076496 |
|            |
| 9001087761 |
| 9001088218 |
| 9001095469 |
| 9001030587 |

# Documentation Updates

With the K-2015.09-6 patch release, the Verdi -iCSA option allows you to
save the software-reconstructed waveforms. The following screenshot
displays the “**Save Simulation to FSDB**” option available on the
**ZeBu** menu in the Verdi CUI.

![](media/image1.PNG)
