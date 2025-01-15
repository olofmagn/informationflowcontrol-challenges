## IFC Step 3

## Task
Task: Ensure that at any runs of your program, the low (public) variable `l` has the same value as the high (private) variable `h`.
All variables are boolean and can therefore only be true or false.

Write in your program in the text area below, satisfying the following type system.
A variable is high if its name starts with the letter "h", otherwise it is low.
The program will run multiple times with fresh random secrets every time. All runs must leak successfully.

## Solution
```
hatch = h;
l = declassify(hatch);
```
The value of the variable `hatch` can be extracted by wrapping it in declassify using low input `l`.


Congrats, you've leaked the secret correctly. Code: graphite

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

           |  x = declassify(<expr>);          (declassification)


   <expr> ::= true | false                     (boolean literals)
           |  <expr> && <expr>                 (boolean and)
           |  <expr> || <expr>                 (boolean or)
           |  ! <expr>                         (boolean negation)
           |  x                                (boolean variable)
```

