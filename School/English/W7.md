# Bios and Bootloader (Markdown file)

## 1. Transition from Bios/UEFI to grub bootloader and kernel initilization:

###  BIOS/UEFI to Grub Transition
- What the hell is BIOS? 
  - BIOS is an acronym for Basic Input/Output system. It is a buildin firmware (a version of software) that determines what a computer can do without accessing disk space. It is always preinstqlled, and is commonly stored on the ROM chip. It contains the basic input and output instructures on how to load computer hardware. It Loads the Operating system into the memory space and conssists of multiple procresses. 
- What the hell is UEFI?
    - Most modern computers use Unified Extensible Firmware Interface (UEFI) firmware which is a successor to BIOS. It is responsible for the same stuff as BIOS. EUFI offers more advanced features over BIOS however such as a secure boot mode, network authentication, and universal graphic drivers.  
- BIOS Boot Process:
    - Power-On Self Test (POST System): This is the system that runs when the machine is powered up. The BIOS performs hardware checks on the machine to ensure all components are properly working.
    - MBR Loading: The Basic Input-Output system reads the MBR or master boot record from the bootable device.
    - GRUB Stage 1: MBR points to the first stage of grub which loads the second stage of it. 
- UEFI Boot Process
    - UEFI initilization: UEFI Firmware initilizes hardware components the same was BIOS does. 
    - EFI system particion (ESP): UEFI reads bootloader files directly from a special partician of the harddrive called the EFI system partician.
    - Grub EFI Executable: UEFI Loads the GRUB EFI binary code without the need for seperate staging like BIOS.
    - For clarification most computers now adays use UEFI boot procress.

### Kernel Initilization Stages and Various Optimizations of the kernel

- What the Hell is the kernel?
    - Put simply, the kernel is a computer program, inside of the operating system. It is the core of the OS and generally has control over everything inside of your computer. Inside of your operating system is it a portion that is responsible for preventing conflicts between different procresses. The Linux kernel is an open source kernel that all GNU/linux systems use. Debian is an exable of the operating system. A full kernel controls all hardware resources via device drivers, and it is the core of your computer. "Wrapping" over that is something known as the shell which allows the user to interface with the kernel. 

- Bootloader to Kernel Handoff:
    - Kernel Loading begins when the grub loads the kernel iso (image) and initial RAM Disk into the memory of the computer. 
    - The GRUB boot loader passes boot parameters to the kernel for it's initilization. 

- Kernel Decompression
    - The compressed kernel image is decrompessed by itself, and is loaded into memory by itself in a stage known as "Unpackig"

- Kernel Initial Initialization:
    - Basic hardware setup is a procress in which the kernel starts up procressor modes, memory management units, and interrupt discriptors 
    - Another step, ensures that a controlled environemnt occurs during the setup period. This environemnt occurs with no interupts allowed. 

- Hardware discovery:
    - The Kernel scans and loads hardware devices and buses into memory. It loads essential drivers for these components (assuming success of the prior step) directly after this. 

- Initramfs Execution:
    - The Initramfs provides a temporary root filesystem for the linux kernel that provides the necessary perms, tools, and scripts to create the real root filesystem.
    - After that the initramf loads any additional kernel modules to memory that are needed for booting the system.

- Switching to the Real Root Filesystem:
    - The kernel, now fully booted, mounts to the real root filesystem. It transitions from initramfs to the actualroot filesystem on the harddrive disk. 
      
- Starting the Init Procress:
    - After the system has been fully initilizated, the real root system has been loaded, the first procress of the computer can run. This is called the Init procress and is always assigned the PID of 1. This code, or application, is started by the kernel. In debian this init procress is systemd. 
      
### Multithreading and Procress scheduling during the boot procress: 
- Single Threaded starts: Early initialization runs as a single threaded program in the CPU which is pretty awesome.
- Once the scheduler of the kernel is initilized the kernel is able to handle multithreading ad multitasking as parallel initialization:
    - Asynchronous Probing: Devices are initialized in parallel where possible.
    - Optimizations that occur during boot.
        - Non-critical drivers are loaded later to speed up boot time. 
        - Higher prioritiy tasks re allowed to interrupt lower prioritiy procresses during boot. 


## 2. Linux Kernel Mechanisms for Process management:

### System calls
System calls are the primary interface between the user applications (in user space) and the kernel (in the kernel space). these systemcalls allow user programs to request services and resources from the kernel. 
- The interface between userspace and kernel space
    - User procresses request kernel services via system calls. 
    - System calls trigger a mode that cause the kernel to switch from user model to kernel space using software interrupts, or other instructurions (CPU-ISA dependent) (I should defiently elaborate on this stuff)
    - The kernel validates arugments and executes the requested system calls on the service. 
- User space and kernel space:
    - The user space is an area of memory where user applications are ran. Programs here have limited priviledges and cannot directly access hardware or kernel memory. 
    - Kernel space is an area of memory where the kernel executes. It has full access to the system's hardware ad can perform priviledges operations. 

### Context Switching
- The procress by which the CPU switches from executing one procress or thread to executing another. This involves saving the current state / context of the running procress, and load the state of the next process to be executed. Context switching allows /usr/local/share/todo/tasks.txt"
for multitasking, multithreading, and multiprocressing. 
- Components of context switching:
    - PCB or procress control block is a data structure maintained by the kernel for each procress. It contains info like PID, CPU registers, Program counter, stack pointers, memory management info, and scheduling parameters.
- The works:
    - The kernel saves the CPU registers of the current procress into the kernel's PCB. This will include the program counter, the stack pointer and other critical info.
    - The kernel's scheduler than determines the next process to run based on scheduling policies and process priorities as defined by the CPU's NICE value, and the CPU's ISA. THe processes that are ready to execute are placed in a ready queue. 
    - The kernel restores the CPU registers and execution context from the PCB of the selected process. THe program's CPU counter and stack pointer are set to the values of the new process. 
    - The CPU begins to execute the new procress from where it last left off. Thus concludes the context switching works. 
    
### Preemption
- Premption is the ability of the OS to interrupt a running procress before it completes its CPU burst (aka the time it needs the CPU for) to schedule another process. This is needed for multitasking. 

### Threading models
- Threads are the smallest unit of execution that can be scheduled by the OS. A procress can contain many threads, all sharing the same address space and resources but are executing independently. There are user space threads and kernel space threads.
- User space threads:
    - Threads managed entirely by the user-space library without the kernel's awareness. 
- Kernel space threadsL
    - THreads that are known and managed by the kernel. This can refer to threads runnning in kernel or user space i they are apped to kernel threads. 
- Models:
    - 1:1 model
        - Each user thread is mapepd to a kernel thread
    - M:M model:
        - Multiple user threads are mapped to a smaller or equal number of kernel threads. 

- Posix Threads (Or pthreads)
    - Definition: 
        - This is a standardized threading APi defined by the portable operating system interface (POSIX). It provides functions for creating, and amanging threads, synchronization primitives, and thread attributes. 
        - In linux it is implimeneted using the 1:1 threading model. Each pthread corresponds to a kernel thread allowing the applications ot utilize multiple core processors effectively. 
          
## 3. Interaction between the Debian file system and the Linux kernel system.

- The virtual file system or VFS. 
  - Conssits of an abstraction layer providing uniform interface for different file systems, and has is capable of Inode operations, and file operations, which are methods  for file metadata handling and methods for reading, writing, and managing files, respectively. 

- The EXT4 file system
    - This is a file system that has intrinsic features like journaling (that logs changes before commiting them), and has an extent based storage that provides dynamic performance by allocating contiguous blocks of data. In the kernel, the metadata works with VFS for inode and directory operations, however for delayed allocation, blocks are defered and allocation is optimized for writing perfomance. 

- The BTRFS file system 
  - This is a different file system that has different features such as Copy on Write which allows for efficient snapshots and cloning. 
    
    
    
## 4. Role of systemd in Debian Process Management 
### SystemD overview:
- Systemd is a modern init system and service manager for Linux Operating systems but not all gnu/linux distros use it. It replaced traditional init systems like SysV init. Systemd is GOATED, and is the prime example of a good init system no matter what anyone says. 
  
- SystemD is the initlizer, the service manager, the resource controller, and the logger for the system. It is the first process started by the linux kernel and it is responsible for the initilization of the user space during the boot procress. It manages starting, stopping, and supervising system services, as well as controlling the linux control groups (cgroups). In addition is provides a system called jounald which is used for all system logging. 
  
- The linux kernel is loaded into memory by the bootloader (GRUB), and the kernel subsystems look for the init procress. The kernel executs the fine is the filesystem /sbin/init, which is a symbolic link to systemd in Debian distros. Systemd then begins the userspace initilization. 

- Similar to runlevels in SysV init, Systemd using targets defined by the system. Graphical.target: is a multiple-user system with a graphical user interface. Multi-user.target: is a multiuser system without a graphical interface. Rescue.target is a single user mode for the rescue partician. 
  
  
## 5. In-Depth Explanation of Linux Kernel Memory Management Mechanisms. 

### overview
- Linux kernel manages the system's memory and provides each process its own virtual address space. THis ensured utilization of ram and handles allocation, deallocation, paging and caching efficiently. 
  
### Paging and virtual memory
- virtual memory allows processes to use more emory than is physically available by using SWAP to extend the ram. Each process operates in its own virtual address space which prevents interference. 
  
- Paging is when memory is divded into fixed size units called pages and frames (virtual and physical memory respectively). The kernel maintains page tables that map virtual pages to physical frames. Multiple level pages can be used by advanced systems for efficiency. 
  
## 6. In depth explanation of low level system information exposed through the proc file system

- The proc filesystem is a virutal filesystem that provides an interface to kernel data structures. It contains runtime system info and is generated on the fly by the system, constantly changing and being read.
- Process info in proc is stored in various ways. 
  - Per process dirs. Insideof proc/[pid] there is data for each running process and it has a directory named after its pid. 
  - CPU info: Contains cpu model, vendor, speed, features, cache sizes, processor info, and more more
  - MEMINFO: Memory usage statisitcs
  - uptime: contains system uptime and idel times.
  - Loadavg: contains load averages over 1, 5, and 15 minutes. 
  - particians: info about disk particians
  - sys: provides runtime configuration of kernel paraets. Paranets are read and modified via sysctl or by manual writing. 
    
## 7. In depth explanation of resource allocation and isolation with cgroups and namespaces. 
### C groups / Control groups:

- Cgroups are a liux kernel feature limiting, accoutning for, and isolating the resource usage of process groups. 
- Namespace: Provides isolation for system resoucres between processes. Includes PID namespaces, mount namespaces, network namespaces, user namespace, ipc namespace, uts namespace. 
- Containers and virtualization
    - Containers are lightweight virtualization using cgroups and namespaces. 
    - Dockers are apps utilzing these features to create isolated environemnts for code to run in. 



