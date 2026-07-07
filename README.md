# LZ77 quine puzzle

This is an implementation of an LZ77 quine puzzle that I first saw on [Will
Greenberg's website](https://wgreenberg.github.io/quine.zip/). This version adds
some extra functionality such as headers and footers, multi level decompression,
and a compile mode.

## Compile mode

Compile mode is a hidden mode which allows you to use certain commands which
compile to LZ77 instructions. Compile mode allows for a much higher level of
abstraction compared to typing raw LZ77 instructions, and makes certain problems
significantly easier. I've hidden the documentation for compile mode here
because I believe that it serves as a massive spoiler for the puzzles. It is
enabled by setting the first line of the input to `COMPILE_MODE`

### compile\_print

Prints directly to compiled output

### quine

    quine length(H) length(T)
    H
    T

When compiled and decompressed once, this will turn into the following:

    H
    quine length(H) length(T)
    H
    T
    T

This is essentially a built-in solution to problems 1 and 2.

### quine\_direct

Similar to `quine`, except the head and tail are directly included in the
compiled code.

### Examples

Puzzle 2 solution

    COMPILE_MODE
    compile_print 1
    <<<<<
    quine 5 3
    a
    b
    c
    d
    <<<<<
    >>>>>
    e
    f
    compile_print 1
    >>>>>
