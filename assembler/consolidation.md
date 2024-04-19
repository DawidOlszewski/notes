# consolidation - linking


## how program compiles

* how and why we have many translation units?
* gcc is `sterownik kompilatora`
* main function is not the first function that is called during code execution - start is

![linking](./imgs/consolidation/linking.png)

## why do we need linkers - modularity
1. we don't need to recompile all code, just one translation unit
2. we can create shared librires - which safe space in disk
3. we can compile multiple files concurrently `make -j $(nproc)`

##  two types of linking:
* static linking - the code can run on its own, without the need for external libraries (after the compilation)
* dynamic linking
  * executable files contain no library code, therefore they need for external libraries during execution
  
## what do linkers do?
* symbol resolution - symbol references to some memory
`![sym-resolution](imgs/consolidation/sym-resolution.png)
* relocation
  ![relocation](./imgs/consolidation/relocation.png)


> [!NOTE]
> `nm` print symbols from object files
> `readelf main.o`

> [!NOTE]
> `objdump -dr main.o`


> [!WARNING]
> `.L2(%rip)` means that after linking phase we will receive insted of `.L2` relative address ti `.L2` from `%rip`

## how ELF file looks like

We have 3 types of ELF files:
* relocative
* executable
* shared libraries


![elf-format](./imgs/consolidation/elf-format.png)
![alt text](./imgs/consolidation/elf-format-2.png)

> [!NOTE]
> `.bss` section instead of 5 mb of unitialized spaced (filled with zeros) its a header with inforamtion that 5mb of zeros is needed

> [!NOTE]
> don't forget about relocation record that are needed to relocate `.L2(%rip)`, which looks like this in `objdump`:
> ![alt text](image.png)
> each section has `.rel` prefix



> [!NOTE]
> co robi `static`:
> dotyczy tylko jednej jednostki translacji

## how linker resolves duplicate symbol definitions

![alt text](./imgs/consolidation/duplicate-symbol.png)
![alt text](./imgs/consolidation/linker-rules.png)


### conclusion - consolidator is stupied

![alt text](./imgs/consolidation/global-vars.png)