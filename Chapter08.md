# The repeat command.
## The "For" command.
- **For(<star>;<Repeat condition>;<jump>)**
    **<command>;**
``` sh
void main()
{
    int i;
    for (i = 0; i < 10; i++)
        printf(“%d\n”, i);
    for (int j = 0; j < 10; j = j + 1)
        printf(“%d\n”, j);
    for (int k = 0; k < 10; k += 2)
    {
        printf(“%d”, k);
        printf(“\n”);
    }
}
```
## The "For" command - Some note.
- The **for** statement is a single statement and can be nested.
- In the **for** statement, there may be no <Start>.
- In a **for** statement, there may be no <jump>.
- In the **for** statement, there may be no <Repeat condition>.
- The **"break"** statement ends the statement.
- The **"continue"** command skips the current iterations.
- Do not add ";" immediately after the "for" command => Equivalent of empty statement.
- The _<Start>, <Repeat condition>, <Jump>_ elements are separated by ";".
- If there are multiple elements in each section, they are separated by a ",".
```sh
for (int i = 1, j = 2; i + j < 10; i++, j += 2)
    printf(“%d\n”, i + j);
```
## The "while" command.
- **While(<Repeat condition>)**
    **<command>;**
- The **while** statement is a single statement and can nested.
- The **while** statement may not execute at all because the first iteration condition is not satisfied.
- Don't add **;** right after the while statement.
- The while statement can be looped endlessly (loop).