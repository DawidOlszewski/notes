# gcc options

> [!NOTE]
> meaning of differnet prefixes:
> * The prefix `-f` stands for "feature". This type of option typically enables or disables specific compiler features or behaviors.
> * The prefix `-z` is a linker option. These options are passed to the linker and control linking behavior rather than direct compilation.
> * The prefix `-m` stands for "machine". These options specify machine-specific features and target architecture characteristics.


* `-fpie`:
    * Purpose: Generate position-independent code (PIC) for executables.
    * Function: Compiles code so that the resulting executable can be loaded at any memory address without modification. This is useful for security features like Address Space Layout Randomization (ASLR).

* `-fstack-protector`:
    * Purpose: Enhance security by adding checks to detect stack buffer overflows.
    * Function: Inserts a guard variable (canary) in functions to detect buffer overflows before the function returns. If the canary value changes, it indicates a buffer overflow, and the program can take action to prevent exploitation.

* `-fno-common`:
    * Purpose: Allocate global variables with static storage by default.
    * Function: Ensures that global variables are defined in exactly one translation unit, preventing certain types of linking errors and potential runtime issues. This option helps catch bugs related to variable definitions and is useful for ensuring code correctness.

* `-fomit-frame-pointer`:
    * Purpose: Optimize code by omitting the frame pointer.
    * Function: Instructs the compiler to omit the frame pointer for functions, freeing up a register for general use and potentially making the code run faster. However, this can make debugging more difficult since the frame pointer is used for generating stack traces.

* `-z noexecstack`:
    * Purpose: Increase security by marking the stack as non-executable.
    * Function: Directs the linker to mark the stack segment of the program as non-executable, preventing execution of code from the stack. This helps mitigate exploits that rely on executing code from the stack, such as certain buffer overflow attacks.

* `-Og`:
    * Purpose: Optimize for debugging experience.
    * Function: Provides a balance between optimization and debuggability. It enables optimizations that do not interfere with debugging, making the code run faster while still being easy to debug.

* `-mno-sse`:
    * Purpose: Disable the use of SSE (Streaming SIMD Extensions) instructions.
    * Function: Prevents the compiler from generating SSE instructions, ensuring compatibility with older CPUs that do not support these instructions. This might be necessary for ensuring the executable runs on a wide range of hardware, particularly older or less capable systems.