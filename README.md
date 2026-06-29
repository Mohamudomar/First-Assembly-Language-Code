# First Assembly Language Code

## Objective

The objective of this activity is to learn how to write and run a simple Assembly language program using the NASM assembler in a Linux environment.

---

## Program Output

The program displays the following text on the screen:

```text
I came,
I saw,
I conquered.
```

---

## Flowchart

```text
+-------+
| Start |
+-------+
    |
    v
+---------------------------+
| Store the message in      |
| the data section          |
+---------------------------+
    |
    v
+---------------------------+
| Print the message to the  |
| screen using Linux        |
| system call               |
+---------------------------+
    |
    v
+---------------------------+
| Exit the program          |
+---------------------------+
    |
    v
+------+
| End  |
+------+
```

---

## Challenges Encountered

One challenge I encountered was understanding how Assembly language communicates with the operating system using registers and Linux system calls. I also had to learn how to define data in the `.data` section and correctly calculate the length of the message before printing it. After understanding the purpose of each register, the program became much easier to follow.

---

## Assembly Code

```asm
section .data
    msg db "I came,", 10, "I saw,", 10, "I conquered.", 10
    len equ $ - msg

section .text
    global _start

_start:
    ; Print the message
    mov eax, 4
    mov ebx, 1
    mov ecx, msg
    mov edx, len
    int 0x80

    ; Exit the program
    mov eax, 1
    mov ebx, 0
    int 0x80
```

---

## Expected Output

```text
I came,
I saw,
I conquered.
```

---

## How to Compile and Run (Linux)

Assemble the program:

```bash
nasm -f elf32 first.asm -o first.o
```

Link the object file:

```bash
ld -m elf_i386 first.o -o first
```

Run the program:

```bash
./first
```

---

## Conclusion

This assignment demonstrates the basics of Assembly language programming by storing a message in memory, printing it to the screen using Linux system calls, and exiting the program successfully. It provides an introduction to NASM syntax, registers, and program structure.
