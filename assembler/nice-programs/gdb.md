# gdb

## `x command`

example: `x/nfu address`

* n (optional): The number of units to display.
    
* f (optional): The format in which to display the memory contents.
    * `x`: Hexadecimal
    * `d`: Decimal
    * `u`: Unsigned decimal
    * `o`: Octal
    * `t`: Binary
    * `f`: Floating point
    * `a`: Address
    * `i`: Instruction (disassemble the memory as instructions)
    * `c`: Character
    * `s`: String
* u (optional): The size of each unit.
    * `b`: Byte (1 byte)
    * `h`: Halfword (2 bytes)
    * `w`: Word (4 bytes)
    * `g`: Giant word (8 bytes)
* address: The starting memory address to examine.


`x/16x $esp+16`
* `info address foo` - napisz informacje o `foo`
* `set disassembly-flavor intel` - zmienia notacje assemblera na `intel` (analogicznie `AT&T` <- `att`)
* `echo "set disassembly-flavor att" >> ~/.gdbinit`

passing a string to a register

```sh
call malloc(14)
set {char[14]} 0x804b010 = "Hello, World!"
set $eax = 0x804b010
```