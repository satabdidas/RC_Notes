# Make Recipes

## Variables in recipes
Use $$ if you want $ to appear in the recipe

```
LIST = one two three
all:
        for i in $(LIST); do \
            echo $$i; \
        done

```

The above will sent $i to the shell.

## Execution
Each recipe is executed in a new sub-shell. Hence if you do a 'cd' in one line, it won't be reflected in the next line.

## Parallel Execution
-j for parallel execution

-k for keep-going even if a recipe fails otherwise make aborts after a recipe fails

### Parallel Output
Usually interspersed since they are printed as soon as they are generated. Some useful options are -

```
--output-sync=line # Group output of each line in the recipe
--output-sync=target # Group output of recipe of a target
--output-sync=recurse # Groups output of each recursive invocation of make
```

### Ignore error in a recipe

```
clean:
        -rm -f *.o
```

Even if the rm fails, make ignores the error.

## Ignored topics
1. .ONESHELL
2. Choosing a SHELL
