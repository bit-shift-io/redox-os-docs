
# Develop 

There look 2 be two methods for debugging.
One for Kernel debugging, you can debug via qemu.
For user-space debugging, you debug inside of Redox OS.

## Kernel Development

https://github.com/redox-os/kernel/blob/master/README.md

gdb


symbol-file /home/melissa/Projects/tryredox/redox/cookbook/recipes/core/kernel/target/x86_64-unknown-redox/build/kernel.sym

target remote localhost:1234

b execve



## User-space Development

### Develop your own app

The docs here work well: 
https://doc.redox-os.org/book/nothing-to-hello-world.html

They show you how to create a new rust user-space app, build it into the redox image and boot into redox to run it.

### Relibc

for relibc

1. open the dir in vscode, run 
    cargo install cbindgen

2. make tests





## Include existing programs

Official docs explain it well here:
https://doc.redox-os.org/book/including-programs.html

For development you will definately wint to include the dev packages:
    ```
    [packages]
    # Add the line below
    gdbserver = {}
    ```

To build your changes and run the emulator:
```make all qemu``` OR for terminal only: ```make all qemu gpu=no```

## Coding & Building

Official docs for developing user-space apps is good:
https://doc.redox-os.org/book/coding-and-building.html

Also note that gdb-redox is included in the image!

## Redoxer

This tool lets you run your rust programs straight in linux, bypassing the need to compile new images to test and debug your programs!

Info on this page: https://doc.redox-os.org/book/coding-and-building.html


## Debugging with GDB

https://www.redox-os.org/news/public-announcement-gdb/

From the above URL under "Usage":

The easiest way to use gdb on Redox, is to uncomment gdbserver and gnu-binutils from your filesystem.toml, and run gdb-redox <absolute filepath> [args...]. It will launch our custom gdbserver and connect to it from gdb over IPC. The “disadvantage” of this is that you’re forced to copy your source code over to Redox if you want pretty symbols and file numbers.

You can also choose to start the standalone gdbserver <absolute filepath> [args...], which will open a socket you can connect to from GDB. This allows you to connect from a host Linux system using your favorite tools like normal, by first running (gdb) target remote :64126 to connect to the running server. This approach forces you to forward :64126 over the network, which can be done by starting Redox with the net=redir flag.