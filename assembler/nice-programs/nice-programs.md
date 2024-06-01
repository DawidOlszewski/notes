# nice programs

# dd

sk**i**p - for input
seek - for output

`status=progress`

`sparse`

# readelf

`-d` - prints content of **d**ynamic sections

`-t` - prints each section de**t**ails 

`-r` - prints **r**elocation sections

`-h` - prints elf **h**eader

`-l` - prints program-headers=segments and its `RWX`



# nm - names
### common symbol records
| symbol type | description              |
| ----------- | ------------------------ |
| B           | Global bss symbol.       |
| b           | Local bss symbol.        |
| D           | Global data symbol.      |
| d           | Local data symbol.       |
| R           | Global read only symbol. |
| r           | Local read only symbol.  |
| T           | Global text symbol.      |
| t           | Local text symbol.       |
| U           | Undefined symbol.        |

### rare symbol records
| symbol type | description                                          |
| ----------- | ---------------------------------------------------- |
| f           | Source file name symbol.                             |
| L           | Global thread-local symbol (TLS).                    |
| l           | Static thread-local symbol (TLS).                    |
| A           | Global absolute symbol.    (for embedded programing) |
| a           | Local absolute symbol.                               |

> [!NOTE]
> Absolute symbol example:\
  `c
  unsigned char buf[128]@0x2000;
  `\
  or\
  `c
  __attribute__((at(0x40001000)))
  `


# objdump
`-s` prints all sections info

`-r` prints relocation info

`-d` disassembly

# more
* size
* pmap
* hd/xxd