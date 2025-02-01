# st (Simple Terminal)

## Overview

**st (Simple Terminal)** is a minimalist terminal emulator developed by the [suckless](https://suckless.org/) community. Designed with simplicity, efficiency, and minimalism in mind, st provides a lightweight and highly customizable terminal experience. Unlike many feature-rich terminal emulators, st adheres to the philosophy of doing one thing well: providing a fast and straightforward interface for command-line operations. Its source code is intentionally kept small, making it easy to understand, modify, and extend according to individual preferences.

---
  
## Table of Contents

1. [Introduction](#introduction)
2. [Background](#background)
3. [Installation](#installation)
4. [Basic Concepts](#basic-concepts)
    - [Terminal Emulator](#terminal-emulator)
    - [Key Bindings](#key-bindings)
5. [Getting Started](#getting-started)
    - [Launching st](#launching-st)
    - [Basic Navigation](#basic-navigation)
6. [Customization and Configuration](#customization-and-configuration)
    - [Configuration File (`config.h`)](#configuration-file-configh)
    - [Building st](#building-st)
    - [Applying Patches](#applying-patches)
7. [Comprehensive Key Bindings](#comprehensive-key-bindings)
    - [Default Key Bindings](#default-key-bindings)
    - [Custom Key Bindings](#custom-key-bindings)
8. [Advanced Features](#advanced-features)
    - [Fonts and Appearance](#fonts-and-appearance)
    - [Clipboard Integration](#clipboard-integration)
    - [Unicode and Internationalization](#unicode-and-internationalization)
    - [Scripting and Automation](#scripting-and-automation)
9. [Tips and Best Practices](#tips-and-best-practices)
10. [Resources](#resources)
11. [Conclusion](#conclusion)

---
  
## Introduction

st is a simple and efficient terminal emulator that focuses on providing a clean and fast interface for users who prefer keyboard-driven workflows. By minimizing unnecessary features and adhering to the Unix philosophy of simplicity, st offers a streamlined environment ideal for developers, system administrators, and power users who seek a no-frills terminal experience. Its extensible nature allows users to tailor the terminal to their specific needs through source code modifications and community-provided patches.

---
  
## Background

Developed by [Anselm R. Garbe](https://github.com/AnselmGarbe) and maintained by the suckless community, st is part of the [suckless](https://suckless.org/) project's mission to create simple, minimalist software that avoids unnecessary complexity. The project's core principles emphasize clarity, simplicity, and frugality, ensuring that each component performs its intended function without bloat.

st operates on the X Window System (X11) and is compatible with a wide range of Unix-like operating systems, including Linux and BSD variants. Its minimalistic design results in a small codebase, typically under 1,500 lines of C code, making it highly maintainable and easy to understand.

---
  
## Installation

### Prerequisites

Before installing st, ensure that your system has the following dependencies:

- **X11 Libraries:** `libx11`, `libxft`, `libxext`
- **Build Tools:** `gcc`, `make`, `pkg-config`

### On Debian/Ubuntu

```bash
sudo apt update
sudo apt install build-essential libx11-dev libxft-dev libxext-dev
```

### On Arch Linux

```bash
sudo pacman -S base-devel libx11 libxft libxext
```

### Cloning and Building st

1. **Clone the Repository:**

    ```bash
    git clone https://git.suckless.org/st
    ```

2. **Navigate to the Directory:**

    ```bash
    cd st
    ```

3. **Customize `config.mk` and `config.def.h` (Optional):**

    - **`config.mk`:** Define installation paths and compilation options.
    - **`config.def.h`:** Customize appearance, key bindings, and behavior.

    **Example:**

    To change the default font, edit the `config.def.h` file:

    ```c
    static char *font = "Fira Code:size=12";
    ```

4. **Build st:**

    ```bash
    make
    ```

5. **Install st:**

    ```bash
    sudo make install
    ```

    **Note:** This installs the `st` binary to `/usr/local/bin/` by default.

### From Package Managers

Some Linux distributions include st in their repositories. For example, on Arch Linux:

```bash
sudo pacman -S st
```

**Note:** Package versions may lag behind the latest source releases.

---
  
## Basic Concepts

### Terminal Emulator

A terminal emulator like st replicates the functionality of traditional hardware terminals within a graphical environment. It allows users to interact with the shell, run command-line applications, and perform various tasks without needing a physical terminal device.

### Key Bindings

Key bindings in st are defined in the `config.def.h` file and are set during compilation. Unlike some other terminal emulators that allow dynamic key binding configurations, st requires users to modify the source code to change key bindings, ensuring a lean and efficient runtime.

---
  
## Getting Started

### Launching st

After installation, you can launch st by simply typing:

```bash
st
```

Alternatively, you can configure your display manager or `.xinitrc` to start st as your default terminal emulator.

### Basic Navigation

- **Open a New Terminal Window:**

    Run `st` from an existing terminal or use your window manager's key bindings to launch applications.

- **Copy and Paste:**

    - **Copy:** Select text with the mouse or keyboard (if configured with patches like `selm`).
    - **Paste:** Use the middle mouse button or keyboard shortcuts defined in `config.def.h`.

- **Scrolling:**

    Enable scrolling with keyboard by configuring scrollback buffer or using patches.

---
  
## Customization and Configuration

### Configuration File (`config.def.h`)

st is configured by editing the `config.def.h` file before building. This file allows customization of appearance, key bindings, behavior, and more.

**Key Configuration Areas:**

- **Appearance:**
  
  Define fonts, colors, padding, and border thickness.

- **Key Bindings:**
  
  Customize or add new key bindings to perform various actions.

- **Behavior:**
  
  Set options like cursor shape, bell behavior, and scrollback buffer size.

**Example `config.def.h` Customizations:**

```c
/* appearance */
static char *font = "Fira Code:size=12";
static char *colorname[] = {
    "#1d1f21", // background
    "#c5c8c6", // foreground
    "#cc6666", // color 1
    "#b5bd68", // color 2
    "#81a2be", // color 3
    "#b294bb", // color 4
    "#8abeb7", // color 5
    "#ffffff", // color 6
};

/* key bindings */
static Shortcut shortcuts[] = {
    /* mask                 keysym          function        argument */
    { ControlMask,         XK_C,           clipcopy,       {.i =  0} },
    { ControlMask,         XK_V,           clippaste,      {.i =  0} },
    { Mod1Mask,            XK_c,           quit,           {.i =  0} },
};
```

### Building st

After customizing `config.def.h`, rebuild and reinstall st to apply changes:

```bash
make clean install
```

**Note:** Ensure you have the necessary permissions (often `sudo`) to install binaries to system directories.

### Applying Patches

st's functionality can be extended through patches provided by the suckless community. Patches modify the source code to introduce new features without requiring a complete overhaul.

**Steps to Apply a Patch:**

1. **Download the Patch:**
   
   Visit the [suckless patches page](https://st.suckless.org/patches/) and download the desired patch.

2. **Apply the Patch:**

    ```bash
    patch < path/to/patch.diff
    ```

3. **Rebuild and Install:**

    ```bash
    make clean install
    ```

**Common Patches:**

- **alpha:** Adds transparency support.
- **scrollback:** Enhances scrollback buffer and navigation.
- **clipbord:** Improves clipboard integration.
- **cursorblink:** Enables cursor blinking.
- **buttonkeys:** Adds mouse button bindings.

**Note:** Always read the patch documentation and ensure compatibility with your st version before applying.

---
  
## Comprehensive Key Bindings

st's key bindings are defined in the `config.def.h` file and are set at compile time. Below is a detailed list of default key bindings and how to customize them.

### Default Key Bindings

By default, st includes minimal key bindings to maintain simplicity. Here are the standard key bindings:

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Mod + Shift + Enter`    | **Open Terminal:** Launch a new terminal window.          |
| `Mod + Shift + C`        | **Close Window:** Close the currently focused window.     |
| `Mod + C`                | **Quit st:** Exit the terminal emulator.                  |
| `Ctrl + Shift + C`       | **Copy:** Copy selected text to the clipboard.            |
| `Ctrl + Shift + V`       | **Paste:** Paste text from the clipboard.                 |
| `Shift + Insert`         | **Paste:** Alternative paste shortcut.                    |
| `Ctrl + Shift + S`       | **Save Screenshot:** Save a screenshot of the terminal.   |
| `Ctrl + Shift + Q`       | **Quick Quit:** Exit st immediately.                      |
| `Ctrl + Shift + N`       | **New Window:** Open a new terminal window.               |
| `Ctrl + Shift + T`       | **New Tab:** Open a new tab (if patched for tab support). |
| `Ctrl + Shift + Arrow`   | **Navigate Panes:** Move focus between split panes.        |
| `Ctrl + Shift + F`       | **Fullscreen:** Toggle fullscreen mode.                   |
| `Ctrl + Shift + R`       | **Reload Config:** Reload the configuration (if patched).  |

**Note:** These key bindings are subject to change based on the applied patches and user customizations.

### Custom Key Bindings

Users can define or modify key bindings in the `config.def.h` file using the `Shortcut` structure.

**Example: Adding a Custom Key Binding to Toggle Transparency**

1. **Apply the `alpha` Patch:**

    Download and apply the `alpha` patch from [st.suckless.org](https://st.suckless.org/patches/).

2. **Define the Key Binding:**

    ```c
    static Shortcut shortcuts[] = {
        /* mask                 keysym          function        argument */
        { ControlMask,         XK_C,           clipcopy,       {.i =  0} },
        { ControlMask,         XK_V,           clippaste,      {.i =  0} },
        { Mod1Mask,            XK_c,           quit,           {.i =  0} },
        { MODKEY,              XK_t,           togglemode,     {.i =  0} }, // Toggle transparency
    };
    ```

3. **Implement the Function:**

    Ensure that the `togglemode` function is defined to handle the transparency toggle.

4. **Rebuild and Install:**

    ```bash
    make clean install
    ```

**Common Customizations:**

- **Changing the Modifier Key:**

    By default, the modifier key (`Mod`) is set to `Alt` (`Mod1Mask`). You can change it to `Super` (`Mod4Mask`) for a more ergonomic setup.

    ```c
    #define MODKEY Mod4Mask
    ```

- **Adding Font Configurations:**

    ```c
    static char *font = "Fira Code:size=12";
    ```

- **Setting Colors:**

    ```c
    static char *colorname[] = {
        "#1d1f21", // background
        "#c5c8c6", // foreground
        "#cc6666", // color 1
        "#b5bd68", // color 2
        "#81a2be", // color 3
        "#b294bb", // color 4
        "#8abeb7", // color 5
        "#ffffff", // color 6
    };
    ```

---
  
## Comprehensive Key Bindings

st's key bindings are minimal by default but can be extensively customized through the `config.def.h` file and various patches. Below is a detailed overview of default and customizable key bindings.

### Default Key Bindings

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Mod + Shift + Enter`    | **Open Terminal:** Launch a new terminal window.          |
| `Mod + Shift + C`        | **Close Window:** Close the currently focused window.     |
| `Mod + C`                | **Quit st:** Exit the terminal emulator.                  |
| `Ctrl + Shift + C`       | **Copy:** Copy selected text to the clipboard.            |
| `Ctrl + Shift + V`       | **Paste:** Paste text from the clipboard.                 |
| `Shift + Insert`         | **Paste:** Alternative paste shortcut.                    |
| `Ctrl + Shift + S`       | **Save Screenshot:** Save a screenshot of the terminal.   |
| `Ctrl + Shift + Q`       | **Quick Quit:** Exit st immediately.                      |
| `Ctrl + Shift + N`       | **New Window:** Open a new terminal window.               |
| `Ctrl + Shift + T`       | **New Tab:** Open a new tab (if patched for tab support). |
| `Ctrl + Shift + Arrow`   | **Navigate Panes:** Move focus between split panes.        |
| `Ctrl + Shift + F`       | **Fullscreen:** Toggle fullscreen mode.                   |
| `Ctrl + Shift + R`       | **Reload Config:** Reload the configuration (if patched).  |

**Note:** These key bindings are default and may vary based on applied patches and user customizations.

### Custom Key Bindings

Users can define additional key bindings or modify existing ones by editing the `config.def.h` file. Below are examples of common custom key bindings.

#### Example: Bind `Ctrl + Shift + T` to Open a New Terminal

```c
static Shortcut shortcuts[] = {
    /* mask                 keysym          function        argument */
    { ControlMask,         XK_t,           spawn,          {.v = termcmd } },
};
```

#### Example: Bind `Mod + Shift + S` to Take a Screenshot

```c
static const char *screenshotcmd[] = { "scrot", "-s", NULL };
static Shortcut shortcuts[] = {
    /* mask                 keysym          function        argument */
    { MODKEY|ShiftMask,    XK_s,           spawn,          {.v = screenshotcmd } },
};
```

### Applying Patches for Enhanced Key Bindings

Patches can introduce additional key bindings and functionalities. For example:

- **scrollback:** Adds key bindings for improved scrollback navigation.
- **buttonkeys:** Enables mouse button interactions.
- **keysym-x:** Adds new key bindings for specific actions.

**Applying a Patch:**

1. **Download the Patch:**
   
   Visit the [suckless st patches page](https://st.suckless.org/patches/) and download the desired patch.

2. **Apply the Patch:**

    ```bash
    patch < path/to/patch.diff
    ```

3. **Rebuild and Install:**

    ```bash
    make clean install
    ```

**Example: Adding Scrollback Key Bindings with the `scrollback` Patch**

After applying the `scrollback` patch, you can use key bindings like:

- `Shift + PageUp` / `Shift + PageDown` to scroll through the terminal history.
- `Ctrl + Shift + Up/Down` to navigate scrollback more efficiently.

---
  
## Advanced Features

### Fonts and Appearance

st allows extensive customization of fonts and colors to match user preferences and system themes.

**Configuring Fonts:**

Edit the `font` variable in `config.def.h`:

```c
static char *font = "Fira Code:size=12";
```

**Setting Colors:**

Define color schemes by modifying the `colorname` array:

```c
static char *colorname[] = {
    "#1d1f21", // background
    "#c5c8c6", // foreground
    "#cc6666", // color 1
    "#b5bd68", // color 2
    "#81a2be", // color 3
    "#b294bb", // color 4
    "#8abeb7", // color 5
    "#ffffff", // color 6
};
```

### Clipboard Integration

By default, st uses the primary selection for copy-paste operations. To enhance clipboard integration, users can apply patches like `clipboard` or use external tools such as `xclip` or `xsel`.

**Example: Using `xclip` for Clipboard Operations**

- **Copy Selected Text:**

    ```bash
    cat file.txt | xclip -selection clipboard
    ```

- **Paste from Clipboard:**

    ```bash
    xclip -selection clipboard -o
    ```

### Unicode and Internationalization

st fully supports Unicode, allowing users to work with a wide range of characters and languages. Ensure that the chosen font in `config.def.h` includes the necessary glyphs for the desired language support.

### Scripting and Automation

While st does not have built-in scripting capabilities, users can automate tasks by leveraging shell scripts and external tools.

**Example: Launching Multiple Applications on Startup**

Create a script `startup.sh`:

```bash
#!/bin/bash
st -e htop &
st -e vim &
st -e ssh user@server &
```

Make it executable:

```bash
chmod +x startup.sh
```

Run the script to launch multiple st instances with different applications.

---
  
## Resources

- **Official st Website:** [https://st.suckless.org/](https://st.suckless.org/)
- **st Git Repository:** [https://git.suckless.org/st](https://git.suckless.org/st)
- **st Source Code:** [https://git.suckless.org/st/tree/config.def.h](https://git.suckless.org/st/tree/config.def.h)
- **st Patches:** [https://st.suckless.org/patches/](https://st.suckless.org/patches/)
- **suckless Wiki:** [https://suckless.org/](https://suckless.org/)
- **st Documentation:** [https://st.suckless.org/doc/](https://st.suckless.org/doc/)
- **Books and Guides:**
    - *Mastering st: A Minimalist Terminal Emulator* by [Author Name] (Hypothetical)
    - *Efficient Workflows with st* by [Author Name] (Hypothetical)
- **Community Forums and Discussions:**
    - [suckless IRC Channel](https://suckless.org/support/)
    - [Reddit r/suckless](https://www.reddit.com/r/suckless/)
  
---
