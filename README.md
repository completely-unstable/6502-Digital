# 6502-Digital

6502 processor in [Digital](https://github.com/hneemann/Digital)

https://github.com/user-attachments/assets/5ff9391d-54b2-40e8-9722-e02027720955

base.dig is set up so that you can enter in your own programs. if you had a program that said:

```
NOP
NOP
NOP
```

first youll need to get the assembled code with something like [Easy 6502](http://skilldrick.github.io/easy6502/). which will give you:

```
0e 0e 0e 00 00 00 ...
```

then format the hex values by prefixing 0x and seperating by commas:

```
0xea,0xea,0xea
```

which this javascript function will do for you:

```
formatHex(hex) {console.log('[' + hex.split(' ').map(h => '0x' + h).join(',') + ']')}
```

then in base.div, right click the 6502 component, and copy paste the hex values in the empty space under the 0s. if you want your program to start somewhere other than 0x0600 then youll have to put that amount of 0s before your program. 

this is not a 1:1 implementation, i designed everything via my own intuition and understanding, so there are nuances in things like how many clock cycles an instruction might take. all testing was done running programs and comparing outputs with the Easy 6502 simulator. this also shares the behaviors: memory 0x0200 - 0x05ff are mapped to display window, 0x00fe generates a random number every cycle, 0x00ff holds the key code of the last key pressed.

also i havent implimented anything that has to do with decimal mode or interrupts. the BRK instruction is simply a NOP that also triggers the built in break component in Digital. 
