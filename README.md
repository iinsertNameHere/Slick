# Slick
 #### Toolchain:
 + [svm](#svm): A VM, just like jvm.
 + [vasm](#vasm): A Compiler that compiles the VM's Assembly language.
 + [vsm](#vsm): Assembly language for the VM.
 + [devasm](#devasm): Disassembler for the bytecode.

### SVM
 A Virtual Machine capable of running bytecode, just like jvm. It is used to run programs generated by [sasmc](#sasmc).

 ```shell
 $ svm.exe [input.sbc]
 ```

### VASM
 The Compiler that compiles [vsm](#vsm) to sbc (slick bytecode) files.

 ```shell
 $ vasm.exe [input.vsm] [output.sbc]
 ```

### VSM
 Assembly language for the Virtual Machine. For examples see [./examples/](./examples).

### DEVASM
 Disassembler for the bytecode generated by the [vasm](#vasm) compiler.

 ```shell
 $ devasm.exe [input.sbc]
 ```