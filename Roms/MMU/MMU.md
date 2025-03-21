# Technical description of the MMU

The MMU is eprom that generates output on the data pins based on the controlled address lines.
Prologic Dos is equipped with a 2764 eprom (8K x 8) as standard.
The eprom has 13 address lines (A0 - A12) but not all address lines are in use.
There is a A13 in the schema, but the pin on a 2764 is not connected

![schema_mmu_default](https://github.com/user-attachments/assets/b6c717c4-9c5f-4dad-9cab-5d6884a245a0)

As can be seen in the diagram, address lines A8 to A12 are always kept high. Address A8 is also connected to the 6821 PIA and could theoretically be made low. 
According to the manual, this would not be the case, it describes that bit 7 of port A must always be high and therefore address line A8 of the MMU is always high.

An 8K eprom has a range of $0000 to $1FFF. 
Based on the fact that address lines A8 to A12 are always high, the consequence is that only the data from $1F00 to $1FFF is used.

Address line A7 is also always high unless it is made low to use Dolphin Dos. The manual explains that this is possible by replacing the KERNAL eprom with the Dolphin Dos variant. 
In addition, a parallel cable will have to be made to the 6522 in the 1541 and the user port of the Commodore 64.

This means that from $1F00 to $1F7F is used as a memory mapping for Dolpin Dos and $1F80 to $1FFF for Prologic Dos.

Addressline A6 determines whether Prologic Dos is on or off.
If this is low, Prologic Dos is turned on and the mapping takes place based on the data in $1F80 to $1FBF. 
If address line A6 is high, the mapping takes place for standard 1541 in $1FC0 to $1FFF

When using Prologic Dos, 35 or 40 tracks can be used for a floppy disk. This setting uses a modified piece from the KERNAL and is determined by the MMU based on address line A5.
The mapping for 35 tracks is classified from $1F80 to $1F9F and 40 tracks from $1FA0 to $1FBF.
In case of A6 high and it's working as a 1541, $1FC0 to $1FDF and $1FC0 to $1FFF contain the same information.

The CPU address lines A11 to A15 are linked to A0 to A4 of the MMU. This allows you to work in 2K blocks in the memory that the CPU uses.

Three data lines of the MMU are linked to the Chip Select of the RAM, Kernal and PIA on PCB from Prologic Dos.
Three data lines are used to use or not use the standard KERNAL and RAM of the 1541.
Two data lines are used to dynamically use pieces of the 16K KERNAL (switch from 35 to 40 tracks)
