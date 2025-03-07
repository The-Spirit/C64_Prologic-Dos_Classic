# C64 PrologicDos Classic

Under development: A redraw of Prologic-Dos Classic pcb's for the Commodore 64.

## Table of contents
[Features](#Features)\
[Versions](#Versions)\
[JANN data technology](#JANN-data-technology)\
[REX data technology](#REX-data-technology)\
[Function key assignment](#Function-key-assignment)\
[LOAD Functions](#LOAD-Functions)\
[Hotkeys](#Hotkeys)\
[Floppy commands](#Floppy-commands)\
[Sources](#Sources)


![Prologicdos Classic C64](https://github.com/The-Spirit/C64_Prologic-Dos_Classic/assets/24958736/c150ad1e-db6c-462c-bafa-ae940cb4de8b)
![PrologicDos Classic 1541](https://github.com/user-attachments/assets/4935c83d-0421-4c12-9d29-dbc47cb35d21)

Prologic DOS and Prologic DOS Classic (labeled version 1.6 or 9612 ) was a parallel fastloader, which consists of a module in the 1541 floppy drive, on the other hand, a module for the Userport or the expansionport  of the C64. 
The whole thing was connected via a parallel cable and made sure that it could supposedly achieve an acceleration of no less than 200 times the normal speed of teh 1541.
It was distributed by Jann data technology, later by the company REX data technology. The fast loader was written by Oliver T. dietz.

## Features
* Acceleration:
  * LOAD up to 65 times faster (measured: 28 times)[1]
  * SAVE without VERIFY up to 65 times faster (measured: 14 times)
  * VERIFY up to 30 times faster
  * File accesses (REL, SEQ) about 30 to 15 times faster
* Floppy monitor
* Function key assignment
* BASIC- and simplified DOS-Command extension:
  * UNNEW-Function
  * Corrected LIST
  * Correct SAVE and REPLACE
* RS232 (V.24) Support
* Built-in Reset-Taster with expandable Reset-Routine
* Expansion port looped
* No rattling or hitting the Write-read head when formatting and errors
* Hardware and software side crash-free switchable to original operating system
* Support for Centronics-Printer over Device address 4
* Usable 35 (664 Blocks) or 40 tracks (749 blocks)

## Versions
- ProLogic DOS (from 1985)
- ProLogic-DOS Classic also for 1541C (version 1.6, from 1987)
- ProLogic-DOS LC (Low Cost Version) for operation at the user port

### JANN data technology
- Prologic-DOS Classic complete with installation and operating instructions, utility disk for 286 DM
- Module for each additional drive 186 DM
- Version for the C128 with switching to the C64 Mode 39 DM surcharge
- Prologic DOS with IEEE-488 (IEC-Bus) for SFD-1001 or hard drives without a Centronics interface 138 DM
- Prologic-DOS-L (Low Cost) for Userport 186 DM
- Copy program Prologic-Nibbler DM 59
- Update to version 1.6: 40 DM

### REX data technology
- REX9610 on the user port for 79 DM (more compatible as an expansion port version !)
- REX9611 Module for the 2nd (each additional) Floppy
- REX9612 at the expansion port for 129 DM

## Function key assignment
- F1  Display one Directory's without program loss
- F2  SYS 4096*
- F3  LIST
- F4  OLD (UNNEW-Function according to NEW or software-side RESET)
- F5  RUN
- F6  OFF (2-step shutdown of Prologic DOS support)
- F7  LOAD loads the first program on disk or the selected program from a directory
- F8  DEV#8/9 Changes the current floppy drive

## LOAD Functions
- LOAD "name",8,0 loads a file to the BASIC start
- LOAD "name",8,0,adresse loads to the decimal specified starting address
- LOAD "name",8,1 (normal without parameter specification) loads to the normal program address
- LOAD "name",8,2 loads with the slower compatibility mode

## Hotkeys
- CTRL + Arrow up Text screen hardcopy
- CTRL + DEL deletes the line from cursor
- CTRL + CRSR right sets the cursor 8 characters to the right
- CTRL + CRSR below places the cursor in the bottom left corner of the screen
- CTRL + Resetbutton bypasses resetvectors at $8000

## Floppy commands
Similar to the DOS-Wedge 5.1:
<pre>@              Error channel output
@$             Directory Calling the directory
@N:Name, ID    New or formatting a floppy disk
@C:New=Old     Copy or rename a file under a new file name
@R:Neuer       Name = Alter Name Rename or rename a file
@S:Name        Scratch or delete the specified file
@I             Initialize diskette
@V             Validate diskette
@XL:Name       Protect file from overwriting (write protection)
@XU:Name       Unprotect the write protection of a protected file
@XR+/-         Enable/disable floppy RAM
@XF+/-         Enable/disable fast data transfer
@XV+/-         Enable/disable VERIFY after write access
@XE+/-         Enable/disable VERIFY after error query
@XD+/-         Enable/disable 35/40 tracks
@XS            Show advanced floppy status: 04,R+,F+,V+,E+,D+,00,00 (Standard values)</pre>

## Sources
1. https://www.c64-wiki.de/wiki/Prologic_DOS_Classic
2. https://blog.worldofjani.com/?p=7092
