# IFC-challenge9
## Task
 Ensure that at any runs of your program, the low (public) variables l1, l2, l3, l4, l5, l6 have the same value as the high (private) variables h1, h2, h3, h4, h5, h6.

All variables are boolean and can therefore only be true or false.
Write in your program in the text area below, satisfying the following type system.
A variable is high if its name starts with the letter "h", otherwise it is low.
Note: This step will be run only once, and always with the same secret. You will need to use this fact.


This is related to `covert timing channel` attacks where information about secret (high-security) variables is leaked through the observable timing behavior of the program. In this code, the `while` loops are conditioned on the value of high-security variables `(h1,h2,h3..., h6)`, which determines how long the program executes or delays before reaching subsequent statements. 

## Solution
```
while ( !h1 ) skip; l1 = true;
while ( h2  ) skip; l2 = false;
while ( !h3 ) skip; l3 = true;
while ( h4  ) skip; l4 = false;
while ( !h5 ) skip; l5 = true;
while ( !h6 ) skip; l6 = true;
```

In particular, we are looking for if execution finished for each test by looking into the execution trace. 
A pattern is that if `!h` the `l1` evaluates to `true` and while `h1` evaluates to `false`.

Program syntax:
```
<program> ::= <topstms>


<topstms> ::= <stm> <stms>

   <stms> ::= <stm> <stms>
           | {empty}

    <stm> ::= skip;                            (a statement with no effect)
           |  x = <expr>;                      (assignment)
           |  { <stm> ... }                    (block statement)
           |  if (<expr>) <stm> else <stm>     (a conditional statement)
           |  if (<expr>) <stm>                (a conditional statement)
           |  while (<expr>) <stm>             (a loop statement)


   <expr> ::= true | false                     (boolean literals)
           |  <expr> && <expr>                 (boolean and)
           |  <expr> || <expr>                 (boolean or)
           |  ! <expr>                         (boolean negation)
           |  x                                (boolean variable)
```
