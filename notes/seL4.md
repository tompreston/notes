# seL4 microkernel
- https://docs.sel4.systems/GettingStarted.html
- https://docs.sel4.systems/Docker.html
- https://docs.sel4.systems/Tutorials/

# Debugging
Stack dump is pretty useless:

    ...
    Booting all finished, dropped to user space
    Caught cap fault in send phase at address (nil)
    while trying to handle:
    vm fault on data at address (nil) with status 0x6
    in thread 0xffffff801ffb5400 "rootserver" at address 0x4022b9
    With stack:
    0x41c950: 0x1
    0x41c958: 0x40a77a
    0x41c960: 0x41ca30
    0x41c968: 0x415798
    0x41c970: 0x0
    0x41c978: 0x0
    0x41c980: 0x0
    0x41c988: 0x40205d
    0x41c990

You can get help by searching for addresses in object dump:

    $ objdump -DS images/hello-1-image-x86_64-pc99
	...
	00000000004022b0 <main>:
	  4022b0:       55                      push   %rbp
	  4022b1:       48 89 e5                mov    %rsp,%rbp
	  4022b4:       b8 00 00 00 00          mov    $0x0,%eax
	  4022b9:       c6 00 58                movb   $0x58,(%rax)
	  4022bc:       bf 08 20 41 00          mov    $0x412008,%edi
	  4022c1:       e8 fc 96 00 00          callq  40b9c2 <puts>
	  4020
	...

The bad instruction is:

	4022b9:       c6 00 58                movb   $0x58,(%rax)
