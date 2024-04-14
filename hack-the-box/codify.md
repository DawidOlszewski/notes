# codify

stty raw -echo

ss -lntp




​
puzzle6:
    subq $24, %rsp
    movq %rsp, %rdi
    call readlong
    leaq 8(%rsp), %rdi
    call readlong
    movq (%rsp), %rax
    cqto
    idivq 8(%rsp)
    xorl %eax, %eax
    testq %rdx, %rdx
    sete %al
    addq $24, %rsp
    ret    
