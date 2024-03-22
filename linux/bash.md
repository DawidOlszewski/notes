# bash

## init program
init - initialize whole system/ cleans up after processes


* ~/.inputrc - file that allows to customize readline library, that is used by many unix programs
* kim jest stoleman-unix robil emacs?
* emacs in an abbreviation for `extensible macros`
* bash executes program **incrementally** - instruction-by-instruction
* by default kernel executes file as binary but if its not an ELF file it will be percived by system as shell script; in first line of script program we put specified interpreter;
* in many scripting languages # is a comment indicator (or at least at first line it is)
* execve is chosing interpreter depending on #!programpath in firs tline



## piping

`prog1 | prog2`

1. a pipe creates a buffer between prog1 and prog2. prog1 uses it as stdout and prog2 uses it as stdin. 
2. When buffer is full - Kernel stops prog1 and starts prog2, that uses that buffer until empty. If prog2 closes stdin fd Kernel sends a sigpipe syscall to prog1
3. by default (if sigpipe handler is not set), process will be killed

## creating temporary files (by process substitution)
example:
```
cmd2 <( cmd1 ) restargs
```
instead of:
```
cmd1 > aslfsaldfjsfs.temp
cmd2 aslfsaldfjsfs.temp restargs
rm aslfsaldfjsfs.temp
```


## bash stupidity

* lexical scope of variables of ordinary programing language is not available in bash
* `bias kulturyowy` in english
* variables are only string envirenmental variables in bash
* environemntal variables has to types that are passed to child processes and not
* `command ls` looks for program not alias or etc
* `#!/usr/bin/env bash -` works like above TODO: check it
* `cp - i`
* getopt -n o co chodzi `-n jak na niby`
* `rsync`
* globy są rozwijane na samym końcu 
* powtóny podział na słowa po niktórych rozwinięcach (TODO: jakich?)
* `Ala*` jeżeli nie ma pliku w tym formacie roziwja się do `Ala*` a nie do pustego stringa
*  globy nie rozwijają się w stringach a zmienne  tak
* W IFS pierwsza litera w stringu bedzie wykorzystywana przez basha do oddzielania słów
* co robi shift
* puste cudzysłowy usuwają możliwość usunięcia tokena
* `x="" foo $x` vs `x="" foo "$x"`
* zmienne środowiskowe podczas prównywania zawsze warto brać w cudzysłwoy
* `if [ a = b ]` vs `[[ ]]`
* w kinie są kamery na podczerwien ykrywające kamery TODO: 
* bash settings `set -o errexit` włącz | `+o` wyłącz 
* `command || exit $` - borrowed from perl
* `shopt vs set`
* rm ignores ..

> [!NOTE]
>  `"$@"` expands into a list of separate parameters. Whereas, `"$*"` is one parameter consisting of all the parameters added together



### lesson nr 4

* every process should have access to read and write to files
* and a handle to file is a file descryptor (ulimit -n prints how many fds process can have)
* fds are refrencing datastructure FILE
* 0,1,2 = stin, stdout, stderr
* symboliczne linki rozwijają się do rożnych ścieżek w zależnosci od processu
* ls -l /proc/self/fd
* `$$` expanses to pid of current process
* ls -l /proc/$$/fd
* bash has to have an open file that he reads from therefore 

* `exec 65535> file1` co robi po co exec
* `exec 65536> file1` error, but file1 gets opened
*  podproess vs process potopmny
*  `2>&1` zawsze czytaj od prawej do lewej `jedynke przypisz do dwójki`
*  `set -o noclobber` `p < b > a` dlatego zawsze warto dawać `p < b >> a`
*  
    ECHO "SLEEP 1" >> ./BASHRC
* p < f | q
* <f p | q
* vs `p | q < f` oesnt' work


o przekierowaniach w bashu 

* co robią te nawiasy w bashu bez `$` czy to sprawi błąd  ()
* metadata of each process sis stored  in Process control block (PCB)
* `" "` cudzysłowy blokują powtórny podział na słowa
* `source file` executes code of `file` in current sehll 
* rc is an abrriviation of 'run command'
* 7
* [ -f file ] && source file
* opcje się pisze przed argumetami

| path1       | path2           |
| ----------- | --------------- |
| /dev/fd     | /proc/self/fd   |
| /dev/stdin  | /proc/self/fd/0 |
| /dev/stdout | /proc/self/fd/1 |
| /dev/stderr | /prco/self/fd/2 |

