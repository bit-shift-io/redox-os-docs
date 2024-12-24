
# Develop 

There look 2 be two methods for debugging.
One for Kernel debugging, you can debug via qemu.
For user-space debugging, you debug inside of Redox OS.

# Kernel Development

# https://github.com/redox-os/kernel/blob/master/README.md

gdb


symbol-file /home/melissa/Projects/tryredox/redox/cookbook/recipes/core/kernel/target/x86_64-unknown-redox/build/kernel.sym

target remote localhost:1234

b execve



# User-space Development

for relibc

1. open the dir in vscode, run 
    cargo install cbindgen

2. make tests