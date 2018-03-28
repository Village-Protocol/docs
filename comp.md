# Compile-Time Options

`-ams_discipline <discipline_name>`  
Specifies the default discrete discipline in VerilogAMS.

`-ams_iereport`  
If information on auto-inserted connect modules (AICMs) is available,
displays this information on the screen and in the log file.

`-assert <keyword_argument>`  
The keyword arguments and what they do are as
follows:

|                 |                                                                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| disable_cover  | Disables coverage for SVA cover statements.                                                                                          |
| dumpoff         | Disables the dumping of SVA information in the VPD file.                                                                             |
| dve             | Enables SystemVerilog assertions tracing in the VPD file that you load into DVE. This tracing enables you to see assertion attempts. |
| enable_diag    | Enables further control of SystemVerilog assertions result reporting with runtime options.                                           |
| filter_past    | Ignores SystemVerilog assertion subsequences containing past operators that have not yet eclipsed the history threshold.             |
| vpiSeqBeginTime | Enables you to see the simulation time that a SystemVerilog assertion sequence starts when using Debussy.                            |
| vpiSeqFail      | Enables you to see the simulation time that a SystemVerilog assertion sequence does not match when using Debussy.                    |

`-C`  
Stops after generating the intermediate C or assembly code.

`-cc <compiler>`  
Specifies and alternative C compiler.

`-CC <options>`  
Works the same as -CFLAGS.

`-CFLAGS <options>`  
Pass options to C compiler. Multiple -CFLAGS are allowed. Allows passing
of C compiler optimization levels.

`-cm line|cond|fsm|tgl|path|branch|assert`  
Specifies compiling for the specified type or types of coverage.

```
The arguments specifies the types of coverage:

  * line Compile for line or statement coverage.

  * cond Compile for condition coverage.

  * fsm Compile for FSM coverage.

  * tgl Compile for toggle coverage.

  * path Compile for path coverage.

  * branch Compine for branch coverage

  * assert Compile for SystemVerilog assertion coverage.
  ```

If you want VCS to compile for more than one type of coverage, use the
plus (+) character as a delimiter between arguments, for example: *cm
line+cond+fsm+tgl
