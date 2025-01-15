# IFC Step 7

## Task
Task: Ensure that at any runs of your program, the low (public) variable l has the same value as the high (private) variable h.
All variables are boolean and can therefore only be true or false.
Write in your program in the text area below, satisfying the following type system.
A variable is high if its name starts with the letter "h", otherwise it is low.
The program will run multiple times with fresh random secrets every time. All runs must leak successfully.

The program have a procedure which allows to ref data into high inputs and then flow the value in the ref data to low input and get the data using `deref`. So we use an intermediate variable `ref x` to store a high property value then we are allowed to assign it to `x` and consequently using `deref`.

## Solution
```
declare ref x: high; ref x = h; l = deref(x);
```

Congrats, you've leaked the secret correctly. Code: hospital

Program syntax:
```
<program> ::= <decls> <topstms>

  <decls> ::= declare proc p(in x : <level>, out y : <level>) <stm> <decls>
           |  {empty}

  <level> ::= high | low


<topstms> ::= <stm> <stms>

   <stms> ::= <stm> <stms>
           | {empty}

    <stm> ::= skip;                            (a statement with no effect)
           |  x = <expr>;                      (assignment)
           |  { <stm> ... }                    (block statement)
           |  if (<expr>) <stm> else <stm>     (a conditional statement)
           |  if (<expr>) <stm>                (a conditional statement)
           |  while (<expr>) <stm>             (a loop statement)

           |  p(<expr>, x);                    (procedure call)


   <expr> ::= true | false                     (boolean literals)
           |  <expr> && <expr>                 (boolean and)
           |  <expr> || <expr>                 (boolean or)
           |  ! <expr>                         (boolean negation)
           |  x                                (boolean variable)
            
```
