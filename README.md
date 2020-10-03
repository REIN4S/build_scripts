# Build Scripts

This repository contains build scripts that I use.  There is language-specific build scripts in each folders.

Here's why Makefile:

* `-j n` option trades off time and computing resources.
* Has accessiblity for every target-dependencies step.
* Prevent growth in the number of files and folders due to over-automation.

## Built With

* Makefile
* Compiler
* Bash
* Diff

## Getting Started

This is an example of build, test for Nim language.

* for Build:

```bash
make
```

* for Test:

```bash
make check
```

* for Clean:

```bash
make clean
```

### License

Distributed under the MIT License. See `LICENSE` for more information.
