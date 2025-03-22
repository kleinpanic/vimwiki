# Systemd Wiki

## Overview - general 
Systemd is a monolithic program. By definition it is a software suite - a collection of computer progrmas that have related functionality. 
Systemd provides an array of system components / functionality / programs for Linux / GNU systems. 
THe main aim of systemd is to unify service configuration and behavior across Linux distributions. Its primary component is a "systemd and service manager" - an init system used to boostrap user-space and user-processes. It also provides replacements for various daemons and utilities, including device management, login management, network connecton management, and event logging. The name systemd adheres to the Unix conventio nof naming daemons by appending the letter d, however according to its creator this was not the purpose behind the name choice.  

Since 2015, the majority of linux distibrutions have adopted systemd, replacing most major init systems such as SysV init, or Runnitd. It has been praised and critized by developers and users of distributons that have adopted it for its stabl, fast out of box solutions for issues, and for its monolithic nature respectively. 
BSD has no such equivalent to my knowledge. This is a major downfall for BSD, if their goal is to expand their userbase. 
Common crititism of systemd is that it suffers from mission creep and bloat, the latter affecting other software (such as the GNOMe desktop - but fuck them anyways), adding dependencies on systemd reducing its compatibility with other Unix-like OSs, making it harder for sysadmins o integrate alternative solutins to their systems. In addition, the complexity of systemd results in a larger "attack surface" reducing the overall security of the platform in general. Concerns have also been raised about Red Hat and its parent company IBm controlling the scene of init systems on Linux. A number of new forked Linux distributions have since been created that use alternative init systems like SysV or OpenRC or RunnitD. Systemd has not been adopted by Unix-Like systems outside of the linux space, like FreeBSD, OpenBSD, and Solaris-oses. 


## Design of Systmed - Wikipedia - need to integrate other sources 

Poettering - the author - describes systemd development as "never finished, never complete, but tracking progres of technology". 
He further said that systemd is unifying "pointless differences between dsibutrions" by providing the following three general functions: 

* A system and service manager
* A software plateform
* The glue between applications and the kernel. 

Systemd includes features like on-demand starting of daemons, snapshot support, process tracking, and inhibitor locks. It is not just the name of the init daemon but also refers to the entire software bundle around it, which, in addition to the systemd init daemon, includes the daemons journald, logind, and networkd, and many other low-level components. In january 2013, Poettering described systemd not as one program, but rather a large software suit that includes 69 individuals binaries. As an integrated sotware suite, systemd replaces the startup sequences and runlevels controleld by the traditional init daemon, along with the shell scripts executed under its control. Systemd also integrates many other services that are common kon linux systems by handling user logns, the system console, device hotplugging (see [udev](udev)), scheduled execution, (replacing [cron](cron)), logging, hostnames and locales. 
Like the init daemon, systemd is a daemon that manages othr daemoins, which, incldude systemd itself, are background processes. Systemd is the first daemon to start during booting and the last daemon to terminate during shutdown. The systemd daemon serves as the root of the user space's [process-tree](process-tree) 
