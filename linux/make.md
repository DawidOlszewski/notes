# make command

```Makefile
main:
    g++ main.cpp -o main
```

```Makefile
main:
    g++ main.cpp -o main

clean:
    rm -f main

dump:
    g++ main.cpp -S
```


### chaining

```Makefile
main:   clean
    g++ main.cpp -o main

clean:
    rm -f main
```

### default envvars

```Makefile
CONFIG_DIR?="/etc/myprogram"

configure:
    echo "${CONFIG_DIR}"
```

### output

**global** silent output (print only things that where redirected to stdout during makefile runtime)
```Makefile
.SILENT:
```

another possibility is to use `@` special operator -

every command preceded in it will be silenet. Especially useful with `echo`

```Makefile
main:
    @echo "main compilation"
    #compile
```