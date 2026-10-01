# AssemblerCalcutator

A small terminal calculator written in x86-64 assembly to practise Linux system calls,
integer conversion, and arithmetic without a C runtime.

![License: MIT](https://img.shields.io/badge/license-MIT-blue)

## 📦 Features

- Implements addition, subtraction, multiplication, and integer division.
- Accepts decimal operands, including negative numbers.
- Converts text input to integers and formats results in assembly.
- Reads from standard input and writes to standard output with Linux system calls.
- Builds with NASM and the system linker; no runtime library is required.

## 🚀 Getting Started

**Requirements**

- Linux on x86-64.
- NASM, the GNU linker (`ld`), and Bash available on your `PATH`.

**Installation**

Clone the repository and enter its directory:

```bash
git clone https://github.com/MrDoodeth/AssemblerCalcutator.git
cd AssemblerCalcutator
```

Install the required tools with your distribution's package manager if they are not
already available. There are no application dependencies to install.

**Quick Start**

```bash
./comlipe.sh program
```

The script assembles `program.asm`, links it, and starts the resulting `program`
executable. It creates `program.o` and `program` in the repository directory.

## 🛠️ Usage

Enter each operand and the operator when prompted. For example:

```text
===== +-*/Calculator/*-+ =====
Enter first variable: 12
Enter operation (+ - * /): *
Enter second variable: 3
Result: 36
```

To build without the helper script:

```bash
nasm -f elf64 program.asm -o program.o
ld -o program program.o
./program
```

**How it works**

- `program.asm` defines the entry point, prompts, input parsing, arithmetic, and output.
- The program calls the Linux `read`, `write`, and `exit` system calls directly.
- `comlipe.sh` is a short build-and-run script; its filename is intentionally shown as
  it appears in the repository.

**Current limitations**

- This is an educational project, not a general-purpose or production-safe calculator.
- Division with a negative first operand can give an incorrect result.
- Integer overflow is not detected; values outside the signed 64-bit range may wrap.
- Empty operands and extra characters after an operator are not rejected consistently.
- Input is read one buffer at a time, so sending all three lines at once through a pipe
  may fail; use the program interactively.
- Invalid input prints an error but currently exits with status `0`.

## 🤝 Contributing

Bug fixes, tests, and documentation improvements are welcome.

1. Fork the repository and create a branch for your change.
2. Test the behaviour you change, including invalid and boundary inputs.
3. Open a pull request describing the change and how you tested it.

## 📜 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for the full text.
