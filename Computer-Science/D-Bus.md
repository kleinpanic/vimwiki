# D-Bus Wiki

## Introduction
D-Bus (short for "Desktop Bus") is a message-oriented middleware mechanism that allows communication between multiple processes running concurrently on the same machine. D-Bus was developed as part of the freedesktop.org project, initiated by GNOME developer Havoc Pennington to standardize services provided by Linux Desktop Environments such as GNOME and KDE. 

The freedesktop.org project also developed a free and open-source software library called libdus, as a reference implmenetation of the specifications. This library is not D-Bus itself, as other implementations of the D-Bus specifications also exist, such as GDbus (GNOME), QtDBus (Qt/KDE), dbus-java and sd-bus (part of systemd). 

### General Information: 

Developer: Red Hat
Initial Release: November 2006
Repository: https://gitlab.freedesktop.org/dbus/dbus
Written In: C
OS: Cross-platform
Predecessors: COBRA, DCOP
Type: IPC Daemon Linux on the Desktop. 
License: GPLv2+ or AFL 2.1
Website: https://www.freedesktop.org/wiki/Software/dbus/

## Overview 

D-Bus is an inter-process communication (IPC) Mechanism initially designed to replace the software component communications systems COBRA and DCOP used by the GNOME and KDE Linux Desktop Environments respectively. The components of these desktop environments are normally distributed in many processes, each providing only one or a few services. These services may be used by regular client applications or by other components of the desktop environment to perform their tasks. 
D-Bus provides a software-bus abstraction that gathers all the communications among a group of processes over a single shared virtual channel. Processes connected to a bus do not know how it is internally implemented, but the D-Bus specifications guarantees that all processes connected to the bus can communicate with each other through it. D-Bus incurs at least a 2.5x performance loss over one-to-one IPC. 
Linux desktop environments take advantage of the D-Bus facilities by instantiating multiple buses, notable: 
* a single system bus, available to all users and proceses of the system, that provides access to system services (i.e services provided by the operating system and also by any system daemons); and 
* a system bus for each user login session that provides desktop services to user applications in the same desktop session, and allows the integraton of the desktop session as a whole. 
A process can connect to any number of buses, provided that it has been granted access to them. In practice, this means that any user process can connect to the system bus and to its current session bus, but not to another user's session buses, or even to a different session bus owned by the same user. The latter restriction may change in the future if all user sessions are combined into a single user bus. 
D-Bus provides additional or simpolifies existing functionality to the applications, incuding information-sharing, modularity and priviledge seperation. For example, information on an incoming video call received through Bluetooth or Skype can be propagated and interpreted by any currently running music player, which can react by muting the volume or by pausing playback until the call is finished. 
D-Bus can also be used as a framework to integrate different components of a user application. For instance, an office suite can communicate through the session bus to share data between a word processor and a spreadsheet. 

## D-Bus specifications. 

### Bus Model 

Every connection to a bus is ientified in the context of D-Bus by what is called a bus name. A bus name consists of two or more dot-seperated string of lettes, digits and underscores - a reverse domain name. An example of a valid bus name is org.freedesktop.NetworkManager. 
When a process sets up a connection to a bus, the bus assigns the connection a special bus name called unique connection name. Bus names of this type are immutable - it is guaranteed they will not change as long as the connection exists - and, more importantly, they cannot be resued during the bus lifetime. This means that no other connection to that bus will ever have assigned such unique conection name, even if the same process closes down the connection to the bus and creates a new one. Unique connection names are easily recognizable because there start with the otherwsie forbidden colon character. An example of a unique connection name is :1.1553 (character )
