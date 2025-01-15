# IFC Step 4

## Task
Ensure that at any runs of your program, the low (public) variable l has the same value as the high (private) variable h.
All variables are boolean and can therefore only be true or false.

Write in your program in the text area below, satisfying the following type system.
A variable is high if its name starts with the letter "h", otherwise it is low.

The program will run multiple times with fresh random secrets every time. All runs must leak successfully.

## Solution

```let  (x = h) in l = x;```

Definition: Explicit flow occurs when the value of a high-security-variable (`h`) is directly assigned or passed to a low-security variable (`l`). This makes the private information contained in `h` observable via the public variable `l`. In this case, the intermediate variable `x` acts as a temporary storage for `h`, but ultimately, the assigment `l=x` directly propagates the private information from `h` to `l`.

This is in contrast to previous exercises with implicit flow.
Implicit flow leaks happen when information about `h` is inferred indirectly, such as through control-flow structures (`if` or loops) rather than direct assigment. For example:

```
if (h) {
    l = true;
} else {
    l = false;
}
```

Congrats, you've leaked the secret correctly. Code: allergy

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

           |  let (x = <expr>) in <stm>        (locally scoped x)


   <expr> ::= true | false                     (boolean literals)
           |  <expr> && <expr>                 (boolean and)
           |  <expr> || <expr>                 (boolean or)
           |  ! <expr>                         (boolean negation)
           |  x                                (boolean variable)
            
```
