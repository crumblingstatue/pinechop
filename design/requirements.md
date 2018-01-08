# Design requirements

## Features

1. Infix arithmetic with arbitrary nesting, and correct operator precedence.

    `3.4 - 43 - -2 * (7.4 - 9.2) ^ 7` should yield `~-162.044`.

2. Function calls

    Ye, there should be function calls. `sqrt(5) * (3 - sin(7))` should yield `~5.239`.

3. Arbitrary precision numbers

    Definitely. Fuck 64 bit floating point.

4. Factorial operator `!`

    geebsawn request

5. User-defineable functions

    Useful shit. Gotta have that.


## Pitfalls to avoid

1. The `-` fiasco.

    Rc tried to treat unary `-` as part of the number during tokenization, but that doesn't work,
    due to ambiguity. Instead, treat it as just the token `-` during tokenization, and apply it
    as a unary negation operator or some shit later down the pipeline.
