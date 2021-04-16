# Inline functions

https://kotlinlang.org/docs/inline-functions.html

Using higher-order functions imposes certain runtime penalties: each function is an object, and it captures a closure. A closure means those variables that are accessed in the body of the function. Memory allocations (both for function objects and classes) and virtual calls introduce runtime overhead.

## Call Site

[Stack Overflow about C-lang inline functions](https://stackoverflow.com/questions/280173/c-inline-functions-and-memory-use)

There are two kinds of memory usage that inline functions will affect:

code size — in general, inlining code will increase how much memory is used to load your program. This is because there will be multiple copies of the generated code scattered around your program. However, this isn't always true -- if your inlined function was only used once, there's little change, and if the inlined function is very small, you could get a net reduction in code size by removing the function call overhead. Also, the function may be reduced in size by the optimizer that's able to remove code that's not used in the particular inline invocation.

stack usage — If your inlined functions have lots of local variables, then you may use more stack space. In C, the compiler usually allocates the stack space for a function once upon entry to the function. This has to be large enough to hold all the local variables that aren't stored in registers. If you call a function out-of-line, the stack for that function is used until it returns, when it's released again. If you inline the function, then that stack space will remain used for the whole life of the uber-function.

Inlining won't affect heap usage, as the same allocations and deallocations would occur for the inlined code as would occur for the non-inlined version.
