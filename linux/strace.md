# strace -system call trace

tool for look inside linux proces

what system calls process is using

`strace -e write ls` - looks for `write` syscalls during new execution of `ls` command

`strace -e write -p pid` - looks for syscalls of specific process with pid=pid

> [!NOTE]
> strace prints arguments and outputs of systemcall on stderr
> and output of command to stdout


## example: 
**fst**:

    nano some-file.txt

**snd**:

    read NANOPID R <<< $(ps -ao pid,command | grep "nano")
    #echo $NANOPID
    strace -e write -p $NANOPID
