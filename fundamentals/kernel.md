# Kernel

Connects the application software to the hardware of a computer: managing i/o requests from software, and translates them into data processing instructions for the CPU and other hardware.

*From: [Wikipedia]()*

> The critical code of the kernel is usually loaded into a protected area of memory, which prevents it from being overwritten by other, less frequently used parts of the operating system or by applications. The kernel performs its tasks, such as executing processes and handling interrupts, in kernel space, whereas everything a user normally does, such as writing text in a text editor or running programs in a GUI (graphical user interface), is done in user space. This separation prevents user data and kernel data from interfering with each other and thereby diminishing performance or causing the system to become unstable (and possibly crashing).

> When a process makes requests of the kernel, the request is called a system call. Various kernel designs differ in how they manage system calls and resources. For example, a monolithic kernel executes all the operating system instructions in the same address space in order to improve the performance of the system. A microkernel runs most of the operating system's background processes in user space, to make the operating system more modular and, therefore, easier to maintain.

> The kernel's interface is a low-level abstraction layer.

![](https://upload.wikimedia.org/wikipedia/commons/8/8f/Kernel_Layout.svg)
