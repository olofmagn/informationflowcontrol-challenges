# IFC Step 5

## Task
Ensure that at any runs of your program, the low (public) variable l has the same value as the high (private) variable h.
All variables are boolean and can therefore only be true or false.
Write in your program in the text area below, satisfying the following type system.
A variable is high if its name starts with the letter "h", otherwise it is low.
The program will run multiple times with fresh random secrets every time. All runs must leak successfully.

## Solution
```
l = true; 

try {
  if (h) throw; else skip; l = false;} catch skip;
```

1. `l = true;`. This sets the variable `l` to `true` initially.
2. `try` block. The code inside the try block will be executed unless an exception is thrown.

`if (h) throw;`: This checks if h is true; then the `throw` statement is executed which will throw an exception and transfer control to the `catch` block.
Since `l` is set to false inside the `try` block, if an exception is caught, `l` will remain `true`.

Congrats, you've leaked the secret correctly. Code: collect

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

           |  throw;                           (throw exception)
           |  try <stm> catch <stm>            (exception handling)


   <expr> ::= true | false                     (boolean literals)
           |  <expr> && <expr>                 (boolean and)
           |  <expr> || <expr>                 (boolean or)
           |  ! <expr>                         (boolean negation)
           |  x                                (boolean variable)
```
            
