https://stackoverflow.com/questions/5309859/how-to-define-an-array-of-functions-in-c

```c
void (*functions[256])();
```

Is an array of function pointers. 

Note, however, that `void func()` isn't a "function that takes no arguments and returns nothing."

It is a function that takes unspecified numbersor types of arguments and returns nothing. Ifyou want "no arguments" you need this:

```c
void (*functions[256])(void);
```
In C++, `void func()` does mean "takes no arguments," which causes some confusion (especially since the functionality C specifies for `void func()` is of dubious value.)

Either way, you should typedef your function pointer. It'll make the code infinitely easier to understand, and you'll only have one chance (at the typedef) to get the syntax wrong:
```c
typedef void (*func_type)(void);
// ...
func_type functions[256];
```
Anyway, you can't assign to an array, but you can initialize an array and copy the data:
```c
static func_type functions[256] = { /* initializer */ };
memcpy(mystruct.functions, functions, sizeof(functions));
```