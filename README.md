# Slick
 #### All Slick Tools:
 + [svm](#svm): A VM, just like jvm.
 + [vasm](#vasm): A Compiler that compiles the VM's Assembly language.
 + [vsm](#vsm): Assembly language for the VM.
 + [devasm](#devasm): Disassembler for the bytecode.

## SVM
 A Virtual Machine capable of running bytecode, just like jvm. It is used to run programs generated by [sasmc](#sasmc).

 ```shell
 $ svm.exe -i [input.sbc]
 ```

*For a list of all Flags:*
 ```shell
 $ svm.exe -h
 ```
<br>

## VASM
 The Compiler that compiles [vsm](#vsm) to sbc (slick bytecode) files.

 ```shell
 $ vasm.exe [input.vsm] [output.sbc]
 ```
<br>

## DEVASM
Disassembler for the bytecode generated by the [vasm](#vasm) compiler.

 ```shell
 $ devasm.exe [input.sbc]
 ```
<br>

## VSM
 Assembly language for the Virtual Machine. For examples see [./examples/](./examples).

| Instruction   | Arguments    | Description                                     |
|--------------|------------|----------------------------------------------------|
| `push`        | `value`      | `Pushes a value on to the stack.`               |
| `dup`         | `addr`       | `Duplicates the value at the given stack addr.` |
| `plus`        | `addr`       | `Adds the top two values on the stack.`         |
| `jmp`         | `label`      | `Jumps to the addr of the given label.`         |
<br>

#### Label definition:

```asm
# Fibonacci numbers
    push 0
    push 1
loop:          # Label definition
    dup 1
    dup 1
    plus
    jmp loop   # Jump to 'loop' label
```