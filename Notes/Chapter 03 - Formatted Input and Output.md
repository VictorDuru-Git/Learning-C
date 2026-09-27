# 3.1 The printf Function

## **Learning Notes (Temporary)**

- Printf must be supplied with the format string +  any values (constants, variables etc) that are to be inserted into the string during printing:
```c
printf(string, expr 1 , expr 2 , …);
```
- An ordinary character in a printf format string, prints exactly as it appears.
- Here Format specifiers (like %d and %f) act as placeholders -> Each placeholder is replaced by the corresponding variable you pass to `printf
```c
int i, j; float x, y;

i = 10;

j = 20;

x = 43.2892f;

y = 5527.0f;

printf("i = %d, j = %d, x = %f, y = %f\n", i, j, x, y);
```


# 3.2 The scanf Function
