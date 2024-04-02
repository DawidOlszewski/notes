# arrays 

> [!NOTE]
> Memory is addressed with bytes

`int val[5] = {1,2,78,100,10};`\

| in-code | in-assembly |
| ------- | ----------- |
| val+1   | val +4      |
| &val[2] | val + 8     |


![mysterious-arrays](./imgs/arrays/mysterious-arrays.png)

> [!CAUTION]
> `int *a[10]` vs `int (*a)[10]`\
> `int* a[10]` is an array of 10 pointers to integers\
> `int (*a)[10]` is a pointer to an array of 10 integers

![row-major-ordering](./imgs/arrays/row-major-ordering.png)

> [!NOTE]
> there are adventages of using fixed size arrays (multidimentional) because compiler can create more efficient code. By faster multiplication. e.g.\
> `T A[i][j]` insted of using `sizeof(T)*i + j` with `imul` it would use some `salq` and `leaq` opts


## sizeof alignof offsetof

### alignof(some_struct or primitive type or array)
takes the minimum primituve subtypre recursively, tells 

> [!NOTE]
> every type has to start at some multiplicity of its size. For example int can be only at positions divisible by 4\
> the padding in the end of some stucter has to be aligned to the max of alignof its variables

