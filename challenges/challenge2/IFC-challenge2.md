# IFC Step 2

## Task
Task: Ensure that at any runs of your program, the low (public) variable `l` has the same value as the high (private) variable `h`.
All variables are boolean and therefore only can be `true` and `false`.
Write in your program in text area below, satisfying the following type system.
A variable is `high` if its name starts with letter "h", otherwise it is low.
The program will run multiple times with fresh random secret every time. All runs must leak succesfully.

## Solution
The code below allows us to branch on high property data and flow sensitive information to a low variable `l` depending on `h`.

```
    if(h) {
        l = true;
    }
    //Then it is low and we should not assign
    else {
    l = false;
    }
```

Congrats, you've leaked the secret correctly. Code: joystick

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
