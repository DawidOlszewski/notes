# MBR

`MBR` -  first sector of a disk (512 B)

`MBR` - consist of :
* bootloader code (446B)
* partition table (64B) - information about 4 partitions (each 16B)
* boot signature (2B)

after that a bootloader is searching for active partition. It will read first sector of that partition, where `boot record` is located. 

# manual partitions


# sticky bits

