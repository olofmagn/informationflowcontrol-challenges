# Challenge 10

# Task
Task: Ensure that at any runs of your program, the low (public) variables l1, l2, l3, l4, l5, l6 have the same value as the high (private) variables h1, h2, h3, h4, h5, h6.

All variables are boolean and can therefore only be true or false.
Write in your program in the text area below, satisfying the following type system.
A variable is high if its name starts with the letter "h", otherwise it is low.
Note: This step will be run only once, and always with the same secret. You will need to use this fact.

## Solution
```
l1 = true;
l2 = false;
l3 = true;
l4 = false;
l5 = false;
l6 = true;
```

Each variable `l` is directly assigned to a fixed value (`true` or `false`), but these assigment might be dependent on high-security conditions or decisions (e.g., via conditions like `if (h1) {l1 = true; }`). If the pattern of `l` values (true/false) reflects sensitive information (e.g., the values of `h1, `h2`, h....n`, then the explicit assigment expose that information to low-security observers. So if `l1 = true` corresponds to `h1 = true`, then observing `l1` reveals `h1`, which violates the security policy.


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
