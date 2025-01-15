# IFC Step 8

## Task
Ensure that at any runs of your program, the low (public) variable l has the same value as the high (private) variable h.
All variables are boolean and can therefore only be true or false.
Write in your program in the text area below, satisfying the following type system.
A variable is high if its name starts with the letter "h", otherwise it is low.
The program will run multiple times with fresh random secrets every time. All runs must leak successfully.

## Solution
```
declare array x: low; x[true] = false; x[h] = true; l = x[true];
```

The key issue is that the second assignment (`x[h] = true`) potentially modifies the same location as the first assigment (`x[true] = false`), but whether it does so depends on the value of `h`.
- If `h = true`, then `x[true]` is overwritten with true during the second assigment.
- If `h = false`, then `x[true]` remains as `false`.

When the public variable l is assigned the value of `x[true]`, it effectively reverals the value of `h`.
Specifically:
- If `l = true` then `h = true`.
- If `l = false` then `l = true`.

Thus, an observer of `l`, which is public, can deduce the value of `h`, which is secret.

Congrats, you've leaked the secret correctly. Code: reckoning

Program syntax:
```
<program> ::= <decls> <topstms>

  <decls> ::= declare array x : <level> ; <decls>
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

           |  x = y[<expr>];                   (reading from an array)
           |  x[<expr>] = <expr>;              (writing to an array)


   <expr> ::= true | false                     (boolean literals)
           |  <expr> && <expr>                 (boolean and)
           |  <expr> || <expr>                 (boolean or)
           |  ! <expr>                         (boolean negation)
           |  x                                (boolean variable)
```


