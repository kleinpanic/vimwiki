# Flipper Zero

## Overivew:

The flipper zero is a portable multi0functional hacking / utility device developed for interacting with access control systems. The device is able to read, copy, and emulate RFID, NFC, Radio remotes, iButtons, digital access keys, IR, and act as a BADusb. It has a GPIO interface which allows enhanced external improvemented. The device's UI embodies a pixel-art dophin virtual pet. The interaction with the virtual pet is the device's core game mechanic. The usage of the device's functions defines the appearance and emotions of the pet. 
In the built-in game, the main mechanism to "upgrade" the dolphin is to use the various hacking tools. While harmless uses (like as a remote control for a television, or carbon dioxide sensor) exist, some of the built-in tools have potential criminal uses, including RFID skimming, Bluetooth spamming (spamming a Bluetooth connection, crashing a person's phone), and emulation of RFID chips such as those found in identification badges, using the built-in radio cloner to open garage doors, unlocking cars, and functioning as a wireless BadUSB.

Flipper Zero is designed for interaction with various types of access control systems, radio protocols, rFID, near-field commuication (NFC), and infrared signals. TO operate the device, a computer or smartphone is not required; it can be controlled via a 5 position D-pad and a seperate back button. Flipper zero has a monochrome orange backlight LCD screen with a resolution of 128 x 64 pixels. For connection with external modules, the degice has GPIO pinholes on the top side. User data and firmware updates are stored on a microSD card. Some actions, such as firmware or user data update, require a connection to a computer or smartphone w/ the developer's software or external softwares installed. 

## Technical Specifications:

The electornic schematics and firmware of the Flipper Zero project are open sources under the GNU General Public License. At the same time ,the device does not fit int othe open-ource hardware category because the printed circuit boards are not open sourced, which does not allow individiauls to make their own copies of the device without knowledge of electrical engineering. 

## Hardware: 

Flipper Zero's hardware consists of four PCB modules connected by flexible cables. The batteryis position i nthe center of the device ebtween three of the PCBs. 

* Main PCB (motherboard) – contains core components, including the main processor (STM32WB55), GPIO breakout pins, LCD display, Sub-GHz chip and its antenna, Bluetooth antenna, microSD card slot, battery controller, USB Type-C port, and membrane switches for the D-pad. All additional PCBs connect to the main PCB via flexible cables.
* Infrared and iButton PCB – a small board equipped with an infrared receiver (TSOP-75338) and three infrared LEDs for transmitting infrared signals. Includes three pogo pins for iButton (1-Wire) tags and a piezo buzzer (BCE-MX8530A) for audio feedback.
* NFC PCB – contains the NFC chip (STM ST25R3916) along with analog circuitry for 125 kHz RFID.
* Dual-Band RFID Antenna PCB – features two passive coil antennas: one for 13.56 MHz NFC communication and another for 125 kHz RFID systems.

### Microcontroller (MCU): 

Flipper Zero is based on a dual-core ARM architecture STM32WB55 microcontroller, which has 256 KB of RAM and 1 MB of Flash storage. The first core is a 64 MHz Cortex-M4 which runs the main firmware. The second core is a 32 MHz Cortex-M0 which runs STMicroelectronics proprietary firmware that implements the Bluetooth Low Energy protocol. Secret keys stored in the Secure Enclave of STM32WB55 are used to decrypt cryptographic keys on the fly, which are then applied to decode Sub-GHz protocols. This mechanism allows the device to handle encrypted communication for Sub-GHz protocols. However, the encryption used is not entirely secure and primarily serves as a form of obfuscation rather than robust protection. Its purpose is to make reverse engineering more challenging, but it does not provide absolute security.


### Sub-GHz Radio: 

For radio transmitting and receiving in the 300–900 MHz radio frequency range, a Texas Instruments CC1101[11] chip is used, which supports amplitude-shift keying (ASK) and frequency-shift keying (FSK) modulations. Unlike software-defined radio, the CC1101 chip cannot capture raw radio signals. This limitation requires the user to pre-configure the modulation parameters before receiving a radio signal, otherwise the signal will be received incorrectly.


### Infrared:

The infrared transceiver in Flipper Zero consists of a digital receiver and an LED circuit. The receiver, based on the TSOP-75338 module, decodes incoming infrared signals. Infrared transmission is managed by three LEDs directly connected to the MCU, which controls the signal output.

### NFC and 125 kHz RFID: 

The NFC subsystem is based on the STM ST25R3916 chip, which is responsible for reading and emulating high-frequency cards. 
The 125 kHz low-frequency RFID functionality in Flipper Zero is implemented primarily through software running on the MCU, without a dedicated RFID chip. It also supports reading RFID tags in the 110–140 kHz range, albeit with a reduced reading distance.

## Hardware Expansion: 

In February 2024, a video game module was released for the Flipper Zero by its makers.[12] The device allows the Flipper to be used as a game controller or connected to a TV and is based around the Raspberry Pi Pico.

## Firmware and Applications: 

The Flipper Zero firmware is based on the FreeRTOS operating system, with its own software abstraction over the hardware layer. The firmware is mostly written in the C programming language, with occasional use of C++ in third-party modules. The system uses multitasking in combination with an event-driven architecture to organize the interaction of applications and services executed in a single address space and communicating through a system of queues and events. The system can be executed from both random-access memory (RAM) and read-only memory (ROM). Execution from RAM is used to deliver over-the-air (OTA) firmware updates.

The firmware consists of the following components:

* FuriCore – provides an API for interaction with the scheduler and multithreading. FuriCore abstracts and extends the functionality of the FreeRTOS scheduler and adds additional system primitives.
* FuriHal – provides an API for interaction with hardware.
* Services and applications – the main functionality of the device. Sub-GHz, Infrared, RFID, NFC, etc are applications for user interaction. Graphical user interface (GUI), command-line interface (CLI), Notification, Storage, etc are additional APIs for applications development.
* A set of libraries and drivers – covers various communication protocols, device drivers, file system drivers, and developer tools.

User and system data is stored in built-in flash memory, which is based on the LittleFS library. Interaction with the file system on the SD card is implemented using the FatFs library.

The build system is based on the SCons tool with additional tooling written in Python. For compilation, the system uses its own open toolchain based on GNU Compiler Collection.

### Sub-GHz:

Flipper Zero has a built-in module that can read, store, and emulate remote controls, allowing it to receive and send radio frequencies between 300 and 928 MHz. These switches, radio locks, wireless doorbells, remote controls, barriers, gates, smart lighting, and other devices can all be operated with these controls. Using Sub-GHz Flipper Zero can also receive and decode the data from many weather stations.

Flipper Zero can receive and transmit radio frequencies in the range of 300-928 MHz with its built-in module, which can read, save, and emulate remote controls. These controls are used for interaction with gates, barriers, radio locks, remote control switches, wireless doorbells, smart lights, and more. Flipper Zero can help you to learn if your security is compromised.

#### Sub-GHz Menu

##### Read: Reads and Decodes signals based on known protocols. If the protocol is static, flipper zero saves the signal. 

With your Flipper Zero, you can read, save, and emulate different types of remote controls with known protocols.

There are remote controls that work on protocols that Flipper Zero doesn’t know yet. Signals from these remotes can be recorded in raw format, saved, and replayed with the Read RAW function.

In Read Mode, flipper zero reads and decodes demodulated signals from remote controls based on known protocols. If the remote's protocl is static, Flipper Zero can save and send the signal. To read, and save the signal from your remote control, do:

1. Go to main menu -> sub-GHz.
2. Press Read and then press the button the remote you want to read. 
[ Insert Image ]
3. When the signal is captured, press ok then press save. 
[ Insert Image ]
4. Name the captured signal, then press Save. 

###### Configuration Menu 






### 125 kHz RFID: 

Flipper Zero is compatible with low-frequency (LF) radio frequency identification (RFID), which is used in supply chain tracking systems, animal chips, and access control systems. LF RFID cards typically don't offer high levels of security, in contrast to NFC cards. Numerous form factors of this technology are available, including plastic cards, key fobs, tags, wristbands, and animal microchips. A low-frequency RFID module in the Flipper Zero can read, save, simulate, and write LF RFID cards.

#### NFC

NFC technology, which is used in smart cards for access control and cards, and digital business cards, is compatible with Flipper Zero. The 13.56 MHz NFC module has the ability to imitate, read, and store these cards. An NFC card is a transponder with a unique identification (UID), and rewritable memory for data storage. When placed close to a reader, NFC cards transmit the needed data.

#### Infrared 

Flipper Zero can read and transmit signals that use infrared light (IR) such as TVs, air conditioners, or audio devices. It can learn and save infrared remote controls or use its own Universal remotes.

#### GPIO and Modules


#### Ibutton: 

The Flipper Zero has an iButton connector to allow it to read and emulate iButton contact keys.

#### badUSB

BadUSB devices have the ability to alter system settings, unlock backdoors, recover data, launch reverse shells, and do any other physical access-based actions. Flipper Zero can function as a BadUSB and, when connected to an insecure computing device, acts as a keyboard-like Human interface device (HID). Commands (the payload) are injected and executed using DuckyScript (the macro scripting language developed as part of the 'USB Rubber Ducky' BadUSB project).

#### U2F

Use the flipper as a second authentication factor for your Google account and others

#### HID Controllers:

Flipper Zero can replace certain HID (human interface device) controllers. This allows it to interact with your phone or computer. It can remotely control media players, computer keyboards or mouse, presentations, and more.

* Keynote: Presentations remote
* Keyboard: Double as a keyboard for a computer
* Media: Controls media on a computer, camera remote control for a phone
* Mouse: Double as a mouse for a computer
* TikTok Controller: Control TikTok app on a phone
* Mouse Jiggler: Duplicate mouse movements on a computer to keep computer showing as active at all times
* PTT : use the flipper as a PTT (push to talk) controller / wireless PTT remote

--- 

## Flipper Zero Documenation: https://docs.flipper.net/?_gl=1*27wxh4*_ga*MTUzMTk4NTM1NC4xNzQ1ODkxMTA5*_ga_GM78S6JK0K*MTc0NjI1ODc4NS41LjAuMTc0NjI1ODc4NS42MC4wLjA.




### 125 kHz RFID

### NFC

### Infrared 

### GPIO & Modules

### iButton 

### BadUSB

### U2F

### Apps

### Flipper Mobile App

### qFlipper

### Developermnet 

### Video Game Modules
