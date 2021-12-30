# Slick
 Slick Toolchain:
 + [svm](#svm): A VM, just like jvm.
 + [asmsc](#asmsc): A Compiler that compiles asms.
 + [asms](#asms): Assembly language for the VM.

### SVM
 A Virtual Machine capable of running bytecode, just like jvm. It is used to run programs generated by [asmsc](#asmsc).
 

*On Windows*:
 ```shell
 > svm.exe [input.sbc]
 ```

### ASMSC
 The Compiler that compiles [asms](#asms) (assembly slick) to sbc (slick bytecode) files.

*On Windows*:
 ```shell
 > asmsc.exe [input.asms] [output.sbc]
 ```

### ASMS
 Assembly language for the Virtual Machine. For examples see [./examples/](./examples).
 