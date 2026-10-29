# NASM Calculator

A terminal calculator in x86-64 NASM assembly for Linux. It uses raw syscalls
(`read`, `write`, `exit`) and no C runtime.

This is an educational project and is not perfect :)

## 📦 Features

- Operations: `+`, `-`, `*`, `/` (integer division) on two operands.
- Signed decimal operands, including a leading `-`.
- Text-to-integer parsing and integer-to-text output written by hand.

## 📋 Requirements

Linux x86-64, `nasm`, `ld`, Bash.

## 🚀 Build and run

```bash
git clone https://github.com/MrDoodeth/nasm-calculator.git
cd nasm-calculator
./comlipe.sh program
```

`comlipe.sh` assembles `program.asm`, links it, and runs the result. Manually:

```bash
nasm -f elf64 program.asm -o program.o
ld -o program program.o
./program
```

## 🛠️ Example

```text
===== +-*/Calculator/*-+ =====
Enter first variable: 12
Enter operation (+ - * /): *
Enter second variable: 3
Result: 36
```

Each prompt is a separate `read`, so enter the values interactively
(piping all three lines at once is not supported).

## 📜 License

MIT, see [LICENSE](LICENSE).
