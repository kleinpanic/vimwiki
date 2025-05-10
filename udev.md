# udev 

udev (userspace /dev) is a device manager for the Linux kernel. As the successor of devfsd and hotplug, udev primarily manages devices nodes in the /dev directory. At the same time, udev also handles all user space events raised when hardware devices are added into the systemor removed from it, including firmware loading, as required by certain devices. 

## Rationale: 

It is an operating system's kernel that is responsible for providing an abstract interface of the hardware to the rest of the sfotware. Being a monolithic kernel, the linux kernel does exactly that, and device driers are part of the liux kernel and make up more than half of its source code. Hardware can be accessed through system calls or over their device nodes.
To be able to deal with peripheral devices that are hotplug-capable in user-friendly ways, a part of the handling all of these hotplug-capable hardware devices was handled voer from the kernel to a daemon running in user-space. running in user space serves security and stability pruposes. 

## Design: 

Device Drivers are part of the linux kernel, in which their primary functions include device discovery, detecting device state changes, and simialr low-level hardware functions
