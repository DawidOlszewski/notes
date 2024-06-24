# How `png` file works?

> [!NOTE]
> it occures that when you are intrested in file format is better to ask google for `png file strucutre` instead of anything else :P

* png file format consists of chunks (which has their specific type and purpuous), which are main building block of a png. There is possibility to create a custom chunks, which can be utilized to inject custom information to a png.

* the first thing in a png file is a sequance of magic bytes (even vefore the first chunk, yes, signature is not a chunk)


# file structure

### each data `chunk` looks like:
* length of data field - big endian (4 bytes)
* chunk type (4 bytes) - depending on letter size can be diffrently interpreted (-> its case sensitive)
* data 
* checksum (4 bytes CRC)

## `IHDR` - image header chunk
* always the data inside the `IHDR` has the same size
* its strucutre:
  * width and hight (4+4=8 byte in total)
  * bit depth (1 byte)
  * color type (1 byte)
  * compression method (1 byte) = 0
  * filter method (1 byte) = 0
  * interlace meth od (1 byte)

> filtering is a method that can save some easy to forseen data in less storage. (i.e 1,2,3,4,5 -> can be saved as arithmetic progresion filter starting from `1` and enging with `5`) 

## `IDAT` - image data

from [w3.org](https://www.w3.org/TR/PNG-Chunks)

> There can be multiple IDAT chunks; if so, they must appear consecutively with no other intervening chunks. The compressed datastream is then the concatenation of the contents of all the IDAT chunks. The encoder can divide the compressed datastream into IDAT chunks however it wishes. (Multiple IDAT chunks are allowed so that encoders can work in a fixed amount of memory; typically the chunk size will correspond to the encoder's buffer size.) It is important to emphasize that IDAT chunk boundaries have no semantic significance and can occur at any point in the compressed datastream. A PNG file in which each IDAT chunk contains only one data byte is legal, though remarkably wasteful of space. (For that matter, zero-length IDAT chunks are legal, though even more wasteful.)

## `IEND` - image end

> [!NOTE]
> `png` supports partially decoding

# read more

https://www.w3.org/TR/PNG-Chunks\
https://www.youtube.com/watch?v=-Rdo8KAHgoE