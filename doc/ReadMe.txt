-------------------------------
ODbgScript English plugin by E3

From
OllyScript plugin v0.92 by SHaG
-------------------------------

1. About OllyScript
2. Status
 2.1 What's new ?
3. Documentation
 3.1 Language
  3.1.1 Reserved variables
  3.1.2 Commands
 3.2 Labels
 3.3 Comments
 3.4 Menus
 3.5 Script Window
4. Integration with other plugins
5. Contact me
6. License and source code
7. Thanks!

------------------------------

1. About ODbgScript
-------------------
ODbgScript is a plugin for OllyDbg, which is, in our opinion, 
the best application-mode debugger out there. One of the best 
features of this debugger is the plugin architecture which allows 
users to extend its functionality. ODbgScript is a plugin 
meant to let you automate OllyDbg by writing scripts in an 
assembly-like language. Many tasks involve a lot of repetitive 
work just to get to some point in the debugged application. By 
using my plugin you can write a script once and for all. 

------------------------------

2. Status
----------------------------

v1.0
OllyScript becomes ODbgScript with the new GUI Window

v0.9
OllyScript has now been downloaded more then 10000 times! That means more then 2Gb of raw
scripting power flowing down the optic cable veins of the Internet. Not bad if you ask me!
The development of the plugin has been a bit slow, I've got a job programming xray systems
which has taken a lot of time. Sorry about that.

2.1 What's new?
---------------
TODO:
  "FOLLOW const" to see any dword data usage (log every command which use it)
  A DLL call function

Known Problems:
  MRU FROM Main Menu is static, so updated only on OllyDbg Restart

1.55.1 (13 May 2007)
x BPHWS second parameter is now optional (default "x")
+ Added GCI Command to Get info on disasm command
+ Added GRO Command Get Relative Offset ("procedure+offset")
+ Added TAB key to Step in Script (S key could "assemble" if ASM window get focus)
+ Added PAUSE key (everywhere) to Pause Script on next command when Application is Running
* negative values fixed
* eip could now be affected without problems
* Resume on Breakpoint fixed (SPACE)

Note: GAPI function could be deleted, hnhu... has not finished the code

1.54.3 (13 May 2007)
+ BUF, STR commands added to convert string to buffer or buffer to string
+ GMI new constants added, (imports, exports, reloc, name, version) see documentation
+ Added Length Information and Hex value to String Variables in Context Menu
+ Enhanced Internal Buffer/String Concatenation : mov test, ##+"123" give #313233# in test
+ Compare Buffer/String is now working
+ Begin Buffer+DW and String+DW (function ADD)
+ Buffer/String Variable Editor is now Binary editor
- Removed MRU menu and some commands from Main Olly Menu
* Internal compare between different types (except buf/str) returns error -2
* Better support in Log Window and Context menu of strings containing "\0"
* removed 00 prefix of dword values in LOG and EVAL commands (%8X to %X)
* OPENTRACE now also opens trace window if not opened
* READSTR documentation update, but this function could be renamed/removed
* FIND commands fix, bad address parameter results 0

1.53.3 (9 May 2007)
+ WRTA has now a third parameter for separator (default \n)
* ASK dlg is now TOPMOST
  no more modal and fixed the crash on close if box was not closed properly
* Added fixes and news from 1.53 Chinese version
 
  + pop,push,test,xchg commands.
  + findcmds(Search for command sequence).
  + Added BPX and BPD functions
  + Added the OPENTRACE function (to open run trace)
  + Added the GAPI function (assign address API)
  + Supports 16bit registers (ax, bx)
  + Added the FINDCMD function (search for command);
  * GN, GCMT, ASM
  * Removed 0 prefix for Hex values in results/values
  * negative hex values support
  * MSG, MSGY no more modal
  
Other differences with Chinese Version :

MRU "Bug" not modified 
  I've made two MRU lists for a good reason, olly doesnt refresh Main Menu
Inline operators are still working in this branch of OdbgScript
Weird ESP Menu not added (i dont know what it is) 
ADD doesnt supports dw+string itoa concatenation

1.50.3 (8 May 2007)
* 4-bytes alignment and speed optimization (thanks Human)
* Changed URL to http://www.woodmann.com/forum in About Box
* Added fixes and news from 1.50 Chinese version : 
  *ASM
  *EXEC,ENDE
  +GMI (added DATABASE, RESBASE, RESSIZE constants)
  *GN
  *LEN bad operand fix
  +DIV,MUL commands
  +READSTR to copy a string (it is possible with MOV too)
  +NEG,NOT asm commands (real asm code)
  +ROL,ROR asm commands but looks like same as SHL, SHR
  *RTU
  *ADD, SHL, SHR, SUB, XOR results to script window

Notes : There are some differences between versions : 
  WRTA doesnt add CR to lines (binary writing)

1.48 (27 May 2006)
+ Added ability to move script execution cursor, double click on a line.

1.47 (06 Feb 2006)
* Fixed GPI command
* GPI CURRENTDIR returns path of debugged app. if empty

1.46 (28 Jan 2006)
* GMEMI,GMI,GPI constants were strings in last versions, no more string quotes needed

1.45 (22 Jan 2006)
+ Added BPHWCALL to clear all hardware breakpoints
* Fixed problems with leading 0 on reversed integers data in find commands
* GMEMI and GMI constants are now in case insensitive
* ASK Cancel button now pauses the script (was abort before)

1.44 (21 Jan 2006)
+ Enhanced GCMT to retrieve automatic comments or comments from analysis
+ Added ITOA and ATOI commands
+ Added GPI (getprocessinfo) command (see docs for info)
* GPA now uses LoadLibraryEx to fix a Comctl32 double load

1.43 (13 Jan 2006)
+ Added GCMT to retrieve comment at specified addr
* Fixed LM function

1.42 (07 Jan 2006) 
+ Script Auto Reset if debugged app is restarted
* Better script uppercase support
* Problem with strings containing brackets

1.41 (21 Dec 2005) 
+ Support for Integer operands in Float Operations (first operand need to be a float)
+ Added Edit Variable dialog for Float vars
# log default type (pointers) is set to DW, was Float in 1.40
# enhanced focus with Ollydbg breakpoints

1.40 (20 Dec 2005) 
+ Added Float variables, registers st(0) <-> st(7), and "in line" operations (+-*/)
  Float operations must contain float operands only
  Float syntax : mov flt, 5.0
# enhanced script window focus
# fixed progress window data if script reloaded is smaller than old one

1.39 (20 Dec 2005) 
# Fixed Ask memory alloc problem
# Always Re-focus to Script windows on "Step" from script.
# Fixed cursor on ret/abort

1.38 (19 Dec 2005) 
+ Added optional LOG command parameter to set log prefix, "" to disable
+ Log windows Auto Scroll
+ Added LC to clear main log window
# LCLR command clears now the script log only
# Script cursor is now normal
# The Log Window is no more called with Script Window from main menu 
# Fixed bugs in mov command with pointers and buffers
# Fixed bug with hex buffer variables containing bytes < 0x10 (no pb with constants) 
# (internal) added backup system for sources in post-link batch

1.35 (12 Dec 2005)
+ Added maxsize optional third parameter to mov Command
+ Added Clear Log Command
+ Enhanced Support of "dump" variables
# fixed some log problems

1.34 (06 Dec 2005)
+ Added Mark for pointers in values column
+ Added Icons to Windows
+ Added Script Log Window
# Fixed Manual Command when no debugged app or no script loaded.
# Modified Load into Run in main and Disasm Menu
# Added Version ressource, and cleaned source architecture

1.33 (06 Dec 2005) (Quick Fix version)
# Some fixes
# Added some constants in code
# Fixed a big bug with string operands containing dword operator

1.32 (05 Dec 2005)
+ Execute Script Command Manually is now possible
+ LCLR command to clear log window
# LOG is now highlighted and displays also message in OllyDbg Status bar
# Updated this Documentation and added a neutral sample script
# Abort Command enhancement

1.31 (05 Dec 2005)
+ Added support of operators in pointers ex: [eax+1]
+ Added support of operator + for strings
+ Decimal values are now supported, with the point (ex: 102.)
+ Variables Menu in Script Window to show/edit variables
+ Edit Script Command in Script Window Context Menu
# Modified script window hotkeys, and added Pause
# SCMPI & SCMP now compares only strings

1.30 (04 Dec 2005)
+ Added support of reg8 & reg16 registers (al,ah...dl,dh,ax,bx,cx,dx,bp,sp,si,di)
+ Added support of operators (+-*/&|^><), operators don't have priority, it's made from left to right
  ">" and "<" are shr and shl, "^" for xor, "&" for and, "|" for or.
+ Variables are now also declared by the destination of mov, if they don't exist
+ Added Result column
+ Value column keeps history of values
+ Enhanced Style of Script Window (current line, jumps, labels, same values)
+ Added KEY to send custom key shorcut to ollydbg (global KEY_DOWN)
+ Added TC to close and delete runtrace
# Fix MRU when a filename contains a comma or { }

1.29 (03 Dec 2005)
+ Added LEN to get string length
+ Added REV to reverse dword bytes
+ Added HANDLE to find a window handle (like "Edit" Boxes) in debugged application
# Script is kept on debugged program restart/change
# Fixed FIND commands to search dwords variables
# MRU on DISASM window is now the real one

1.28 (26 Nov 2005)
+ Added "Load Script" in DISASM Context Menu
+ Added "ALLOC size" and "FREE addr, size" to (un)allocate memory page
# Modified Run Script to Load in Main MRU
# MRU is no more showing full path of scripts
# ASK now returns string len in $RESULT_1

1.27 (25 Nov 2005)
+ Added REF to get References to selected command
+ Added OPCODE command to get command bytes, text and size at specified address
# Better comments handling
# Better #inc handling (using also current script path)
# PREOP now works in memory block, not only in code block

1.26 (24 Nov 2005)
+ Added Optionnal Start Address to "FINDMEM what [, StartAddr]" (to continue global search)
+ Added PREOP command to get previous command address before specified address

1.25 (22 Nov 2005)
+ Added FINDMEM to search into the whole memory
+ Added WRT (write a file) and WRTA (append) commands: WRT file, data
+ Added GMEMI function (Memory Block Informations)
# GPA now returns 0 and continue if the API is not found, $RESULT_2 set to Proc name if found.
# fixed OllyDbg focus problem
# fixed path of created files when full path given
# fixed FIND binary wildcards, broken in 1.24

1.24 (19 Nov 2005)
+ FIND and FINDOP supports strings and string vars arguments
+ MSG and MSGYN have now Cancel button to pause script (MSGYN returns 2 if canceled)
# Script will now pause instead of stop when error is returned from commands
+ Script Breakpoints (to "debug" a script)
+ Added Real "Load Script" to start paused (script window)
+ Added Step/Resume and Hotkeys (script window)

1.23 (14 Nov 2005)
+ Enhanced String by Address support for commands (ex: gpa [nAddr],"KERNEL32.DLL")
+ lm, load Dump file to mem: lm, 0x401000, 0x100, "test.bin" (MetaCore)
# fix the dm, lm, dmp, dpe 's default dump path to debugging app's path. (MetaCore)
# fix dm, ...the open file parameter is incorrect, will add mess "0a 0d" at each lines tail. (MetaCore)
# fix all dump related function's parameter check, so when the real mem is smaller then gived 
  dump length, will not add mess data at the end, and the $result also catched the real dump size. (MetaCore)

1.22 (11 Nov 2005)
+ Added SCMP and SCMPI for string comparaison (SCMPI for case insensitive)
# Restored CMP string comparaison to case sensitive

1.21 (8 Nov 2005)
+ Remember Script Window Position & State
+ Automatic Scroll to follow script
+ Context Menu (Real MRU/Follow) in Script Window
# Fix table refresh
# CMP string compare is now case insensitive

1.20 (7 Nov 2005)
+ Script Window with values and eip
+ CMP now accepts strings from address

1.10 (5 Nov 2005)
+ MRU List

1.0 (4 Nov 2005)
# ODbgScript (VC6 Based)

0.92
+ New commands: ASK, BPL, BPLCND, COB, COE, EVAL, EXEC/ENDE, GN, TICND, TOCND
+ Execution of code in the target process context
+ String concateration with ADD or EVAL
+ Input box
+ Logging breakpoints
+ Removal of EOB and EOE
+ Tracing with condition
+ Get name of address
# ASM now returns assembled length in $RESULT
# Fixed pause crash bug
# Fixed bug with JBE, hopefully it was the last of the Jxx bugs
# OllyScript now REQUIRES OllyDbg v1.10. No other versions are officially supported.

------------------------------

3. Documentation
----------------
Example script (sample.osc) is available with this release. 
The script will break on LoadLibray call to debug a SHELL32.DLL function. 
Try it on mspaint.exe

3.1 Language
------------
The scripting language of OllyScript is an assembly-like language.

In the document below, src and dest can be (unless stated otherwise):
 - Constant in the form of a hex number withot prefixes and suffixes (i.e. 00FF, not 0x00FF or 00FFh)
   For decimal values, use the point (i.e. 100. 128.)
 - Variable previously declared by VAR, or are declared with MOV
 - A 32-bit register (one of EAX, EBX, ECX, EDX, ESI, EDI, EBP, ESP, EIP).
   A 16-bit register (one of AX, BX, CX, DX, SI, DI, BP, SP)
   A 8-bit register (one of AL, AH, ... DL, DH)
 - A memory reference in square brackets (i.e. [401000] points to the memory at address 401000, 
	[ecx] points to the memory at address ecx).
 - A flag with an exclamation mark in front (one of !CF, !PF, !AF, !ZF, !SF, !DF, !OF)
 - Sometimes byte strings are required. those are scripted as #6A0000# (values between two #) and 
	must have an even number of characters.
   Some byte strings can contain the wildcard '?', for exampla #6A??00# or #6?0000#
 - A combinaison of this values with operators :

You can use operators in your scripts, +-*/&|^>< for dword and + to concatenate strings.
 - Operators > and < are shr and shl (>> and << in C/C++)
 - Operator ^ is XOR 
 - Operator & is AND
 - Operator | is OR

3.1.1 Reserved variables
------------------------

$RESULT
-------
Return value for some functions like FIND etc.
$RESULT_1 and $RESULT_2 are available for some commands.

$VERSION
--------
Contains current version of OllyScript
Example
	cmp $VERSION, "0.8"
	ja version_above_08

3.1.2 Commands
--------------

#INC file
---------
Includes a script file in another script file
Example:
	#inc "anotherscript.txt"
	
#LOG
----
Enables logging of executed commands.
The commands will appear in OllyDbg log window, and will be prefixed with -->
Example:
	#log

ADD dest, src
-------------
Adds src to dest and stores result in dest
Example: 
	add x, 0F
	add eax, x
	add [401000], 5
	add y, " times" // If y was 1000 before this command then y is "1000 times" after it

AI
--
Executes "Animate into" in OllyDbg
Example:
	ai

ALLOC size
----------
Allocate new memory page, you can read/write and execute.
Example
    alloc 1000
	free $RESULT, 1000

AN addr
-------
Analyze module which contains the address addr.
Example:
	an eip // Same as pressing CTRL-A

AND dest, src
-------------
ANDs src and dest and stores result in dest
Example: 
	and x, 0F
	and eax, x
	and [401000], 5

AO
--
Executes "Animate over" in OllyDbg
Example:
	ao

ASK question
------------
Displays an input box with the specified question and lets user enter a response.
Sets the reserved $RESULT variable (0 if cancel button was pressed).
You have also the length in $RESULT_1 (divised by 2 for hex entries)
Example:
	ask "Enter new EIP"
	cmp $RESULT, 0
	je cancel_pressed
	mov eip, $RESULT
	
ASM addr, command
-----------------
Assemble a command at some address.
Returns bytes assembled in the reserved $RESULT variable
Example:
	asm eip, "mov eax, ecx"

ASMTXT addr, file
-----------------
Assemble a text asm file at some address.
Example:
	asmtxt EIP, "myasm.txt"

ATOI str [, base=16.]
-----------------
Converts a string to integer
Returns the integer in the reserved $RESULT variable
Example:
	itoa "F"
	itoa "10", 10.

BC addr
-------
Clear unconditional breakpoint at addr.
Example:
	bc 401000
	bc x
	bc eip

BP addr
--------
Set unconditional breakpoint at addr.
Example:
	bp 401000
	bp x
	bp eip

BPCND addr, cond
----------------
Set breakpoint on address addr with condition cond.
Example:
	bpcnd 401000, "ECX==1"
	
BPL addr, expr
--------------
Sets logging breakpoint at address addr that logs expression expr
Example:
	bpl 401000, "eax" // logs the value of eax everytime this line is passed
	
BPLCND addr, expr, cond
-----------------------
Sets logging breakpoint at address addr that logs expression expr if condition cond is true
Example:
	bplcnd 401000, "eax", "eax > 1" // logs the value of eax everytime this line is passed and eax > 1
	
BPMC
----
Clear memory breakpoint.
Example:
	bpmc

BPHWC addr
----------
Delete hardware breakpoint at a specified address
Example:
	bphwc 401000
	
BPHWS addr, [mode]
------------------
Set hardware breakpoint. Mode can be "r" - read, "w" - write or "x" - execute (default).
Example:
	bphws 401000, "x"

BPRM addr, size
---------------
Set memory breakpoint on read. Size is size of memory in bytes.
Example:
	bprm 401000, FF

BPWM addr, size
---------------
Set memory breakpoint on write. Size is size of memory in bytes.
Example:
	bpwm 401000, FF

BUF var
-------
Converts string/dword variable to a Buffer
Example: 
	mov s, "123"
	buf s
	log s // output "#313233#

CMP dest, src
-------------
Compares dest to src. Works like it's ASM counterpart.
Works with strings too (case sensitive)
Example: 
	cmp y, x
	cmp eip, 401000

CMT addr, text
--------------
Inserts a comment at the specified address
Example:
	cmt eip, "This is the entry point"

COB
---
Makes script continue execution after a breakpoint has occured (removes EOB)
Example:
	COB

COE
---
Makes script continue execution after an exception has occured (removes EOE)
Example:
	COE

DBH
---
Hides debugger
Example:
	dbh

DBS
---
Unhides debugger
Example:
	dbs

DEC var
-------
Substracts 1 from variable
Example:
	dec v

DIV op1, op2
------------
Sets op1 with op1/op2
Example:
	div var, 2

DM addr, size, file
-------------------
Dumps memory of specified size from specified address to specified file (default path set from opened app.)
Example:
	dm 401000, 1F, "c:\dump.bin"

DMA addr, size, file
-------------------
Dumps memory of specified size from specified address to specified file appending to that file if it exists
Example:
	dma 401000, 1F, "c:\dump.bin"

DPE filename, ep
----------------
Dumps the executable to file with specified name.
Entry point is set to ep.
Example:
	dpe "c:\test.exe", eip

EOB label
---------
Transfer execution to some label on next breakpoint.
Example:
	eob SOME_LABEL

EOE label
---------
Transfer execution to some label on next exception.
Example:
	eob SOME_LABEL

ESTI
----
Executes SHIFT-F7 in OllyDbg.
Example:
	esti

ESTO
----
Executes SHIFT-F9 in OllyDbg.
Example:
	esto

EVAL
----
Evaluates a string expression that contains variables.
The variables that are declared in the current script can be enclosed in curly braces {} to be inserted.
Sets the reserved $RESULT variable
Example:
	var x
	mov x, 1000
	eval "The value of x is {x}" // after this $RESULT is "The value of x is 00001000"

EXEC/ENDE
---------
Executes instructions between EXEC and ENDE in the context of the target process.
Values in curly braces {} are replaced by their values.
Example:
// This does some movs
var x
var y
mov x, "eax"
mov y, "0DEADBEEF"
exec
mov {x}, {y} // mov eax, 0DEADBEEF will be executed
mov ecx, {x} // mov ecx, eax will be executed
ende
// This calls ExitProcess in the debugged application
exec
push 0
call ExitProcess
ende
ret

FILL addr, len, value
---------------------
Fills len bytes of memory at addr with value
Example:
	fill 401000, 10, 90 // NOP 10h bytes

FIND addr, what
---------------
Searches memory starting at addr for the specified value.
When found sets the reserved $RESULT variable. $RESULT == 0 if nothing found.
The search string can also use the wildcard "??" (see below).

Example:
	find eip, #6A00E8# // find a PUSH 0 followed by some kind of call
	find eip, #6A??E8# // find a PUSH 0 followed by some kind of call

FINDCMD addr, cmd
-----------------
Assemble and search asm command
Results are same than FIND Command
Example:
	findcmd 401000, "nop"

FINDCMDS addr, cmd
------------------
Assemble and search asm serie of commands.
Results are same than FIND Command
Example:
	findcmds 401000, "nop;nop;nop"

FINDOP addr, what
-----------------
Searches code starting at addr for an instruction that begins with the specified bytes. 
When found sets the reserved $RESULT variable. $RESULT == 0 if nothing found.
The search string can also use the wildcard "??" (see below).
Example:
	findop 401000, #61# // find next POPAD
	findop 401000, #6A??# // find next PUSH of something
	findop 401000, "1" // = #61#

FINDMEM what [, StartAddr]
--------------------------
Searches whole memory for the specified value.
When found sets the reserved $RESULT variable. $RESULT == 0 if nothing found.
The search string can also use the wildcard "??" (see below).
Example:
	findmem #6A00E8# // find a PUSH 0 followed by some kind of call
	findmem #6A00E8#, 00400000 // search it after address 0040.0000

FREE addr, size
----------
Free memory allocated by ALLOC.
Example
    alloc 1000
	free $RESULT, 1000

GAPI addr #BETA#
---------
## Chinese Translation ## 
Obtains the code place API call information
The API information saves in preservation variable $RESULT.
If the symbolic name is a API function, then
$RESULT saves the API information
$RESULT_1 save link base/storehouse (for instance kernel32)
$RESULT_2 save symbolic name (for instance ExitProcess).
$RESULT_3 save calling location (for instance call xxxxx)
$RESULT_4 save destination

Notice: This and the GN difference is GN must point to the IAT address
But GAPI gives the code address to be possible directly to obtain API
Also has, if you have gotten down the software break point in here, please first clear the break point to use this sentence again, because the software break point modified the code is CC
If here does not clear here the software break point, will create this not to be able the very good recognition.
Example:
	GAPI 401000 (call kernel32.ExitProcess)
	GAPI the EIP // examined whether the current code is API calls, is not then returns to 0

GBPR
----
Gets last breakpoint reason, affects $RESULT with dword value
(see plugin.h PP_EVENT for values...)

GCI addr, info
--------------
Gets information about asm command
"info" can be DESTINATION for Destination of jump/call/return
Example:
	GCI eip, DESTINATION

GCMT addr
---------
Gets the comment, automatic comment or analyse's comment at specified code address

GMEMI addr, info
----------------
Gets information about a memory block to which the specified address belongs.
"info" can be MEMORYBASE, MEMORYSIZE or MEMORYOWNER (if you want other info in the future versions plz tell me).
Sets the reserved $RESULT variable (0 if data not found).
Example:
	GMEMI addr, MEMORYBASE // After this $RESULT is the address to the memory base of the memory block to which addr belongs

GMI addr, info
--------------
Gets information about a module to which the specified address belongs.
"info" can be :
MODULEBASE, MODULESIZE, CODEBASE, CODESIZE, MEMBASE, MEMSIZE, 
ENTRY, NSECT, DATABASE, RELOCTABLE, RELOCSIZE
RESBASE, RESSIZE, IDATABASE, IDATATABLE, EDATATABLE, EDATASIZE
and strings NAME, PATH, VERSION
 (if you want other info in the future versions plz tell me).
Sets the reserved $RESULT variable (0 if data not found).
Example:
	GMI eip, CODEBASE // After this $RESULT is the address to the codebase of the module to which eip belongs

GN addr
-------
Gets the symbolic name of specified address (ex the API it poits to)
Sets the reserved $RESULT variable to the name. If that name is an API
$RESULT_1 is set to the library (ex kernel32) and $RESULT_2 to the name of the API (ex ExitProcess).
Example:
	gn 401000
	
GO addr
-------
Executes to specified address (like G in SoftIce)
Example:
	go 401005

GPA proc, lib
-------------
Gets the address of the specified procedure in the specified library.
When found sets the reserved $RESULT variable. $RESULT == 0 if nothing found.
Useful for setting breakpoints on APIs.
Example:
	gpa "MessageBoxA", "user32.dll" // After this $RESULT is the address of MessageBoxA and you can do "bp $RESULT".

GPI key
-------
Gets process information, one of :
HPROCESS,PROCESSID,HMAINTHREAD,MAINTHREADID,MAINBASE,PROCESSNAME,EXEFILENAME,CURRENTDIR,SYSTEMDIR

GRO addr
--------
Get Relative Offset
When found sets the reserved $RESULT variable. $RESULT == 0 if nothing found.

HANDLE x, y, class
---------------------
Returns the handle of child window of specified class at point x,y (remember: in hex values).

INC var
-------
Adds 1 to variable
Example:
	inc v

ITOA n [, base=16.]
-----------------
Converts an integer to string
Returns the string in the reserved $RESULT variable
Example:
	itoa F
	itoa 10., 10.

JA label
--------
Use this after cmp. Works like it's asm counterpart.
Example:
	ja SOME_LABEL

JAE label
---------
Use this after cmp. Works like it's asm counterpart.
Example:
	jae SOME_LABEL

JB label
--------
Use this after cmp. Works like it's asm counterpart.
Example:
	jb SOME_LABEL

JBE label
---------
Use this after cmp. Works like it's asm counterpart.
Example:
	jbe SOME_LABEL

JE label
--------
Use this after cmp. Works like it's asm counterpart.
Example:
	je SOME_LABEL

JMP label
---------
Unconditionally jump to a label.
Example:
	jmp SOME_LABEL

JNE label
---------
Use this after cmp. Works like it's asm counterpart.
Example:
	jne SOME_LABEL

KEY vkcode [, shift [, ctrl]]
--------------------------
Emulates global keyboard shortcut.
Example:
	key 20
	key 20, 1 //Shift+space
	key 20, 0, 1 //Ctrl+space

LBL addr, text
--------------
Inserts a label at the specified address
Example:
	lbl eip, "NiceJump"

LC
----
Clear Main Log Window

LCLR
----
Clear Script Log Window

LEN str
--------------
Get length of a string
Example:
	len "NiceJump"
	msg $RESULT

LM addr, size, filename
-------
load Dm file to mem
LM is the opposite of the DM command
Example:
  lm 0x401000, 0x100, "test.bin"

LOG src [,prefix]
-------
Logs src to OllyDbg log window.
If src is a constant string the string is logged as it is.
If src is a variable or register its logged with its name.
You can replace default prefix with the optional second parameter.
Example:
	log "Hello world" // The string "Hello world" is logged
	var x
	mov x, 10
	log x // The string "x: 00000010" is logged.
	log x, "" // The string "00000010" is logged.

MOV dest, src [,maxsize]
-------------
Move src to dest.
Src can be a long hex string in the format #<some hex numbers>#, for example #1234#.
Remember that the number of digits in the hex string must be even, i.e. 2, 4, 6, 8 etc.
Example: 
	mov x, 0F
	mov y, "Hello world"
	mov eax, ecx
	mov [ecx], #00DEAD00BEEF00#
	mov !CF, 1
	mov !DF, !PF
	mov [403000], "Hello world"

MSG message
-----------
Display a message box with specified message
Example:
	MSG "Script paused"

MSGYN message
-------------
Display a message box with specified message and YES and NO buttons.
Sets the reserved $RESULT variable to 1 if YES is selected and 0 otherwise.
Example:
	MSGYN "Continue?"

MUL op1, op2
------------
Sets op1 with op1*op2
Example:
	mul op1, 10

NEG op
------
Assembly Operation "neg eax"

NOT op
------
Assembly Operation "not eax"

OR dest, src
------------
ORs src and dest and stores result in dest
Example: 
	or x, 0F
	or eax, x
	or [401000], 5

OPCODE addr
-----------
OPCODE sets the $RESULT variable to the opcode bytes, $RESULT_1 variable to mnemonic opcode (i.e. "MOV ECX,EAX") 
and $RESULT_2 to the length of the opcode. 
If an invalid opcode appears, $RESULT_2 should be 0. 
addr is increased by the length of the opcode (disassemble command). 
With this function you can step forward through code. 
Example: 
	opcode 00401000

OPENTRACE
---------
Opens run trace window

PAUSE
-----
Pauses script execution. Script can be resumed from plugin menu.
Example:
	pause

POP dw
------

Retrieve dword from stack

PREOP addr
----------
Get asm command line address just before specified address.
Attention: Will not give real executed command eip before the jump.
Example:
	preop eip

PUSH dw
-------
Add dword to stack

READSTR str, len
-------
Copy len chars of str into $RESULT

REF addr
--------
REF addr works as "Find references to .. Selected command" and "Find references", Ctrl R, in OllyDbg.
$RESULT variable is set to the first reference addr 
$RESULT_1 to the opcode (text asm command) 
$RESULT_2 to the comment (like reference window). 
Repeat "REF addr" until $RESULT=0 to get next refs
Example:
	continue:
		REF eip
		log $RESULT
		log $RESULT_1
		log $RESULT_2
	cmp $RESULT,0
	jne continue

REPL addr, find, repl, len
--------------------------
Replace find with repl starting att addr for len bytes.
Wildcards are allowed
Example:
	repl eip, #6a00#, #6b00#, 10
	repl eip, #??00#, #??01#, 10
	repl 401000, #41#, #90#, 1F

RET
---
Exits script.
Example:
	ret

REV
---
Reverse dword bytes.
Example:
	rev 01020304
	//$RESULT = 04030201

ROL op, count
------
Assembly Operation "rol eax, cl"
save in the target (first) operand.

ROR op, count
------
Assembly Operation "ror eax, cl"
Example:
	mov x, 00000010
	ROR x, 8 

RTR
---
Executes "Run to return" in OllyDbg, [Ctrl+F9] operation.
Example:
	rtr

RTU
---
Executes "Run to user code" in OllyDbg, [Alt+F9] operation.
Example:
	rtu

RUN
---
Executes F9 in OllyDbg
Example:
	run

SCMP dest, src
-------------
Compares strings dest to src. Works like it's ASM counterpart.
Example: 
	cmp x, "KERNEL32.DLL"
	cmp [eax], "Hello World"

SCMPI dest, src
-------------
Compares strings dest to src (case insentitive). Works like it's ASM counterpart.
Example: 
	cmp sVar, "KERNEL32.DLL"
	cmp [eax], "Hello World"

SETOPTION
---------
Chinese Translated :
Assigns out the debugging to set the (Option) menu, after setting, after determination continues to execute the script
Notice: This option is for may in execute in the script process to be possible to assign out the debugging setting to be unusual, track and so on setting

SHL dest, src
-------------
Shifts dest to the left src times and stores the result in dest.
Example:
	mov x, 00000010
	shl x, 8 // x is now 00001000

SHR dest, src
-------------
Shifts dest to the right src times and stores the result in dest.
Example:
	mov x, 00001000
	shr x, 8 // x is now 00000010

STI
---
Execute F7 in OllyDbg. STep Into.
Example:
	sti

STO
---
Execute F8 in OllyDbg. STep Over.
Example:
	sto

STR var
-------
Converts variable to a String

SUB dest, src
-------------
Reduce src from dest.
Example: 
	sub x, 0F
	sub eax, x
	sub [401000], 5

TC
--
Cancels run trace in OllyDbg
Example:
	tc

TEST dest,src
-------------
Performs a logical AND of the two operands updating the flags register without saving the result.
(Modifies Flags: CF OF PF SF ZF (AF undefined))

TI
--
Executes "Trace into" in OllyDbg, CTRL-F7 in OllyDbg.
Example:
	ti

TICND cond
----------
Traces into calls until cond is true
Example:
	ticnd "eip > 40100A" // will stop when eip > 40100A

TO
--
Executes "Trace over" in OllyDbg
Example:
	to

TOCND cond
----------
Traces over calls until cond is true
Example:
	tocnd "eip > 40100A" // will stop when eip > 40100A

VAR
---
Declare a variable to be used in the script.
Example: 
	var x

XOR dest, src
-------------
XORs src and dest and stores result in dest
Example: 
	xor x, 0F
	xor eax, x
	xor [401000], 5

XCHG dest, src                                 
--------------
Exchanges contents of source and destination.         

WRT file, data
--------------
Write to file (replace existing one) the only accepted symbol is "\r\n"
Numbers are wrote as strings... for the moment
Example: 
	wrt "out.txt", "Data:\r\nOk\r\n"
	wrt sFile, ebx

WRTA file, data [, separator]
-----------------------------
Append to file, default separator is "\n"
Example: 
	wrta sFile, "hello world"
	wrta sFile, ABCD, ""
	wrta sFile, "Windows CR, "\r\n"

3.2 Labels
----------
Labels are defined bu using the label name followed by a colon.
Example:
	SOME_LABEL:

3.3 Comments
------------
Comments can be put anywhere and have to start with "//". 
Block comments between "/*" and "*/"

3.4 Menus
---------
The main OllyScript menu consists of the following items:
- Run script...: lets the user select a script file and starts it
- Abort: aborts a running script
- Pause: pauses a running script
- Resume: resumes a paused script
- About: shows information about this plugin

3.5 Script Window
-----------------
The Script Window was introduced with ODbgScript, it enables you to debug
and see progression of your script.
You can set script breakpoints, debug the script, edit variables and also 
execute commands manually.

------------------------------

4. Integration with other plugins
---------------------------------
You can call OllyScript from your plugin and make it execute a script.
Use something like the source code below:

HMODULE hMod = GetModuleHandle("ODbgScript.dll");
if(hMod) // Check that the other plugin is present and loaded
{
	// Get address of exported function
	int (*pFunc)(char*) = (int (*)(char*)) GetProcAddress(hMod, "ExecuteScript");
	if(pFunc) // Check that the other plugin exports the correct function
		pFunc("myscript.txt"); // Execute exported function
}

------------------------------

5. Contact us
-------------
To contact us you can post your question in the forum or go on IRC 
and message Epsylon3 or SHaG on EFnet. 

You can also mail SHaG to shag-at-apsvans-dot-com.

------------------------------

6. License and source code
--------------------------
Soon I'm going to armadildo this plugin and charge an awful lot of money
for it! :P Seriously, you are free to use this plugin and the source code however 
you see fit. However please name me in your documentation/about box and if 
the project you need my code for is on a larger scale please also notify 
me - I am curious.

------------------------------

7. Thanks!
----------
I'd like to thank all the wonderful people who reported bugs, wrote scripts, came
with improvement ideas etc. 

R@dier for the great dumping engine.

shERis, nick_name, MetaCore, XanSama, arnix, hila123, bukkake, Human
for ideas and bug report on the new ODbgScript

And of course Olly for developing this great debugger!

------------------------------