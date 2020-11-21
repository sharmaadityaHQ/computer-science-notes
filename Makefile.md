## Makefile

- Most open source projects use `make` to compile a final executable binary, which can then be installed using `make install`.
- The `make` utility is useful if we want to run or update a task when certain files are updated.
- `Makefile` defines set of tasks to be executed.
- Syntax of a `rule` in the `Makefile`
```
target: prerequisites
<TAB> recipe
```
- Only the first target in the `Makefile` is the default target and is executed when we run `make`. `all` can be used to call other targets. We define all the targets that are not files in `.PHONY`.  

Example:
```
.PHONY: all say_hello generate clean

all: say_hello generate

say_hello:
        @echo "Hello World"

generate:
        @echo "Creating empty text files..."
        touch file-{1..10}.txt

clean:
        @echo "Cleaning up..."
        rm *.txt
```

