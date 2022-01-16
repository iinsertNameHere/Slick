# Slick
 #### All Slick Tools
 + [mvm](#mvm): A VM, just like jvm.
 + [masm](#masm): A Compiler that compiles the VM's Assembly language.
 + [msm](#msm): Assembly language for the VM.
 + [demasm](#demasm): Disassembler for the bytecode.

 #### Meaning
 + *mvm* **->** `Minimalistic Virtual Machine`
 + *masm* **->** `Minimalistic Assembler`
 + *msm* **->** `Minimalistic Assembly`
 + *demasm* **->** `Decompile Minimalistic Assembly`

## MVM
 A Virtual Machine capable of running bytecode, just like jvm. It is used to run programs generated by [masm](#masm).

**Features:**
- *Stack size:* **942**
- *Turing Complete*
- *Own asm language*

<br>

 ```shell
 > svm.exe -i [input.sbc]
 ```

*For a list of all Flags:*
 ```shell
 > svm.exe -h
 ```
<br>

## MASM
 The Compiler that compiles [msm](#msm) to sbc (slick bytecode) files.

 ```shell
 > masm.exe [input.vsm] [output.sbc]
 ```
<br>

## DEMASM
Disassembler for the bytecode generated by the [masm](#masm) compiler.

 ```shell
 > demasm.exe [input.sbc]
 ```
<br>

## MSM
 Assembly language for the Virtual Machine. For examples see [./examples/](./examples).

| Instruction | Arguments                      | Description                                                                                                                        |
|-------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| push        | `value`                        | Pushes a value on to the stack.                                                                                                    |
| dup         | `addr`                         | Duplicates the value at the given stack `addr`.                                                                                    |
| swap        | `addr`                         | Swaps the top value and the value at the given `addr`.                                                                             |
| drop        | NONE                           | Removes the top value from the **stack**.                                                                                          |
| plusi       | **stack:** `a, b`              | Adds the top two values on the **stack**. (for integers)                                                                           |
| minusi      | **stack:** `a, b`              | Subtracts the top two values on the **stack**. (for integers)                                                                      |
| multi       | **stack:** `a, b`              | Multiplies the top two values on the **stack**. (for integers)                                                                     |
| divi        | **stack:** `a, b`              | Divides the top two values on the **stack**. (for integers)                                                                        |
| plusf       | **stack:** `a, b`              | Adds the top two values on the **stack**. (for floats)                                                                             |
| minusf      | **stack:** `a, b`              | Subtracts the top two values on the **stack**. (for floats)                                                                        |
| multf       | **stack:** `a, b`              | Multiplies the top two values on the **stack**. (for floats)                                                                       |
| divf        | **stack:** `a, b`              | Divides the top two values on the **stack**. (for floats)                                                                          |
| eq          | **stack:** `a, b`              | Pushes *ZERO* on the stack if the top two values are not equal, else it pushes *ONE*.                                              |
| not         | **stack:** `a`                 | Reverses the top value on the stack. e.g. `0 to 1 and 1 to 0` (for integers, 0-1)                                                  |
| gef         | `a, b`                         | Pushes *ZERO* on the stack if the top value on the stack is grater or equal to the second value. (for floats)                      |
| gei         | `a, b`                         | Pushes *ZERO* on the stack if the top value on the stack is grater or equal to the second value. (for integers)                    |
| jmp         | `label` or `addr`              | Jumps to the the given `label` or `addr`.                                                                                          |
| jmpif       | `label` or `addr`              | Jumps to the the given `label` or `addr` if the top value on the stack is *ZERO*.                                                  |
| call        | `label` or `addr`              | Jumps to the the given `label` or `addr` and pushes the *addr* from the instruction after the current instruction on to the stack. |
| ret         | **stack:** `addr`              | Jumps to the the given `addr` (top value on the stack).                                                                            |
| ncall       | `functionId` **stack:** `args` | Calls a native function depending on the given `functionId` and parses the `args` from the **stack** to it.                        |
| hlt         | *NONE*                         | Stops the execution.                                                                                                               |
<br>

#### Label definition:

```asm
# Fibonacci numbers
push 0
push 1
# Label definition
loop:
    dup 1
    dup 1
    plus
    jmp loop   # Jump to 'loop' label
```
*or*
```asm
# Fibonacci numbers
push 0
push 1
# Label definition
loop: dup 1
      dup 1
      plus
      jmp loop   # Jump to 'loop' label
```

#### Call definition:
```asm
jmp main

# Function
add:
    swap 2
    plusf
    swap 1
    ret

main:
    push 10
    push 5
    call add # Calls the functions
    ncall 3 # Prints the result
    hlt
```

#### Code example:
```asm
# Hello World program in msm:
push 0
push 13     # \n
push 33     # !
push 100    # d
push 108    # l
push 114    # r
push 111    # o
push 87     # W
push 32     # SPACE
push 111    # o
push 108    # l
push 108    # l
push 101    # e
push 72     # H

printLoop:
    push 1
    dup 1
    gei
    jmpif nextStep # If not 0 print char
    jmp end # Else jmp to end
    nextStep:
    ncall 0
    jmp printLoop

end:
    hlt
```