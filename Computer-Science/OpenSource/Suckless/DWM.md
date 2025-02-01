# DWM (Dynamic Window Manager)

## Overview

**DWM (Dynamic Window Manager)** is a minimalist and highly efficient tiling window manager for X11, developed by the [suckless](https://suckless.org/) community. Designed with simplicity, speed, and minimalism in mind, DWM allows users to manage their workspace using keyboard shortcuts, minimizing reliance on the mouse. Its lightweight nature ensures low resource consumption, making it ideal for users seeking a streamlined and customizable desktop environment.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Background](#background)
3. [Installation](#installation)
4. [Basic Concepts](#basic-concepts)
    - [Layouts](#layouts)
    - [Tags](#tags)
5. [Getting Started](#getting-started)
    - [Launching DWM](#launching-dwm)
    - [Basic Navigation](#basic-navigation)
6. [Key Bindings](#key-bindings)
    - [Modifier Key](#modifier-key)
    - [Default Key Bindings](#default-key-bindings)
7. [Customization and Configuration](#customization-and-configuration)
    - [Configuration File (`config.h`)](#configuration-file-configh)
    - [Building DWM](#building-dwm)
    - [Applying Patches](#applying-patches)
8. [Advanced Features](#advanced-features)
    - [Status Bar](#status-bar)
    - [Multi-Monitor Support](#multi-monitor-support)
    - [Scripting and Automation](#scripting-and-automation)
9. [Tips and Best Practices](#tips-and-best-practices)
10. [Resources](#resources)
11. [Conclusion](#conclusion)

---

## Introduction

DWM is a dynamic tiling window manager that efficiently organizes windows in a non-overlapping layout, maximizing screen real estate and enhancing productivity. Unlike traditional window managers that rely heavily on mouse interactions, DWM emphasizes keyboard-driven workflows, allowing users to navigate, resize, and manage windows swiftly through predefined key bindings.

---

## Background

Developed by [Anselm R. Garbe](https://suckless.org/dev.shtml), DWM is part of the [suckless](https://suckless.org/) project, which advocates for simplicity, clarity, and frugality in software design. DWM adheres to the philosophy of doing one thing well, providing a minimalistic environment without unnecessary bloat. Its source code is concise (typically under 2000 lines), making it easy to understand, modify, and extend according to individual preferences.

DWM operates on the X11 windowing system, making it compatible with a wide range of Unix-like operating systems. Its minimalist design ensures rapid performance, even on older hardware, while its configurability allows users to tailor the environment to their specific needs.

---

## Installation

### Prerequisites

- **X11:** Ensure that the X Window System is installed on your machine.
- **Build Essentials:** Tools like `gcc`, `make`, and `pkg-config` are required to compile DWM from source.
- **Libraries:** Dependencies such as `libx11`, `libxft`, and `libxinerama` should be installed.

### On Debian/Ubuntu

```bash
sudo apt update
sudo apt install build-essential libx11-dev libxft-dev libxinerama-dev
```

### On Arch Linux

```bash
sudo pacman -S base-devel libx11 libxft libxinerama
```

### Cloning and Building DWM

1. **Clone the Repository:**

    ```bash
    git clone https://git.suckless.org/dwm
    ```

2. **Navigate to the Directory:**

    ```bash
    cd dwm
    ```

3. **Customize `config.h` (Optional):**

    Before building, you can customize settings by editing the `config.h` file. See the [Customization and Configuration](#customization-and-configuration) section for more details.

4. **Build DWM:**

    ```bash
    make
    ```

5. **Install DWM:**

    ```bash
    sudo make install
    ```

    **Note:** This installs the `dwm` binary to `/usr/local/bin/` by default.

### From Package Managers

Some Linux distributions offer DWM in their repositories. For example, on Arch Linux:

```bash
sudo pacman -S dwm
```

**Note:** Package versions may lag behind the latest source releases.

---

## Basic Concepts

### Layouts

DWM supports multiple window layouts to organize open windows efficiently. The primary layouts include:

- **Tile:** The default tiling layout where one window is master (larger) and others are stacked.
- **Monocle:** Maximizes the focused window to occupy the entire screen.
- **Floating:** Allows windows to float freely without automatic tiling.

### Tags

Instead of traditional workspaces or virtual desktops, DWM uses **tags** to categorize and manage windows. Each window can be assigned one or more tags, and users can view windows based on their tags. By default, DWM provides nine tags, labeled `1` through `9`.

---

## Getting Started

### Launching DWM

To start DWM, you typically set it as your default window manager in your display manager or initiate it from a `.xinitrc` file.

**Using `.xinitrc`:**

1. **Edit/Create `.xinitrc`:**

    ```bash
    nano ~/.xinitrc
    ```

2. **Add the Following Line:**

    ```bash
    exec dwm
    ```

3. **Start X Session:**

    ```bash
    startx
    ```

### Basic Navigation

- **Open Terminal:**
  
  Press `Mod + Shift + Enter` to launch the default terminal emulator.

- **Close Window:**
  
  Press `Mod + Shift + c` to close the focused window.

- **Switch Focus:**
  
  Use `Mod + h`, `Mod + j`, `Mod + k`, `Mod + l` to navigate between windows.

- **Change Layout:**
  
  Press `Mod + t` to toggle between tiling and floating layouts.

---

## Key Bindings

### Modifier Key

- **Default Modifier Key (`Mod`):** `Alt (Mod1)` or `Super (Mod4)`
  
  DWM's key bindings are initiated by the `Mod` key. Users can configure this in the `config.h` file.

### Default Key Bindings

Below is a comprehensive table of DWM's default key bindings. These bindings are categorized based on their functionalities.

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Mod + Enter`            | **Open Terminal**: Launch the default terminal emulator. |
| `Mod + d`                | **Launch dmenu**: Open the dmenu launcher for applications. |
| `Mod + Shift + c`        | **Close Window**: Close the currently focused window.     |
| `Mod + j`                | **Focus Next Window**: Move focus to the next window.     |
| `Mod + k`                | **Focus Previous Window**: Move focus to the previous window. |
| `Mod + h`                | **Increase Master Area**: Increase the size of the master area. |
| `Mod + l`                | **Decrease Master Area**: Decrease the size of the master area. |
| `Mod + Shift + j`        | **Swap with Next Window**: Swap the focused window with the next window. |
| `Mod + Shift + k`        | **Swap with Previous Window**: Swap the focused window with the previous window. |
| `Mod + Shift + Enter`    | **Toggle Floating**: Toggle the focused window between floating and tiling mode. |
| `Mod + t`                | **Change Layout**: Toggle between tiling and floating layouts. |
| `Mod + Space`            | **Cycle Layouts**: Cycle through available layouts.       |
| `Mod + 1` to `Mod + 9`    | **View Tag**: Switch to the specified tag (1-9).          |
| `Mod + Control + r`      | **Restart DWM**: Restart DWM without terminating sessions. |
| `Mod + Control + q`      | **Quit DWM**: Exit DWM and terminate the X session.       |

**Note:** These key bindings can be customized in the `config.h` file to suit individual preferences.

---

## Customization and Configuration

### Configuration File (`config.h`)

DWM's behavior and appearance are configured through the `config.h` file, which is part of its source code. To customize DWM, users edit this file and recompile the window manager.

**Key Configuration Areas:**

- **Appearance:**
  
  Define fonts, colors, and window borders.

- **Key Bindings:**
  
  Customize or add new key bindings to perform various actions.

- **Layouts:**
  
  Define and modify window layouts.

- **Tags:**
  
  Configure the number and labels of tags.

**Example `config.h` Customizations:**

```c
/* appearance */
static const char *fonts[]          = { "monospace:size=10" };
static const char dmenufont[]       = "monospace:size=10";
static const char col_gray1[]       = "#222222";
static const char col_gray2[]       = "#444444";
static const char col_gray3[]       = "#bbbbbb";
static const char col_cyan[]        = "#005577";
static const char *colors[][3]      = {
    /*               fg         bg         border   */
    [SchemeNorm] = { col_gray3, col_gray1, col_gray2 },
    [SchemeSel]  = { col_gray1, col_cyan,  col_cyan  },
};

/* tagging */
static const char *tags[] = { "1", "2", "3", "4", "5", "6", "7", "8", "9" };

/* key definitions */
#define MODKEY Mod1Mask
#define TAGKEYS(KEY,TAG) \
    { MODKEY,                       KEY,      view,           {.ui = 1 << TAG} }, \
    { MODKEY|ControlMask,           KEY,      toggleview,     {.ui = 1 << TAG} }, \
    { MODKEY|ShiftMask,             KEY,      tag,            {.ui = 1 << TAG} }, \
    { MODKEY|ControlMask|ShiftMask, KEY,      toggletag,      {.ui = 1 << TAG} },

/* helper for spawning shell commands */
#define SHCMD(cmd) { .v = (const char*[]){ "/bin/sh", "-c", cmd, NULL } }

/* commands */
static const char *dmenucmd[] = { "dmenu_run", "-fn", dmenufont, "-nb", col_gray1, "-nf", col_gray3, "-sb", col_cyan, "-sf", col_gray1, NULL };
static const char *termcmd[]  = { "st", NULL };

static Key keys[] = {
    /* modifier                     key        function        argument */
    { MODKEY,                       XK_d,      spawn,          {.v = dmenucmd } },
    { MODKEY|ShiftMask,             XK_Return, spawn,          {.v = termcmd } },
    { MODKEY,                       XK_j,      focusstack,     {.i = +1 } },
    { MODKEY,                       XK_k,      focusstack,     {.i = -1 } },
    { MODKEY,                       XK_h,      setmfact,       {.f = -0.05} },
    { MODKEY,                       XK_l,      setmfact,       {.f = +0.05} },
    { MODKEY|ShiftMask,             XK_j,      pushdown,       {0} },
    { MODKEY|ShiftMask,             XK_k,      pushup,         {0} },
    { MODKEY,                       XK_Return, zoom,           {0} },
    { MODKEY,                       XK_Tab,    view,           {0} },
    { MODKEY|ShiftMask,             XK_c,      killclient,     {0} },
    { MODKEY,                       XK_t,      setlayout,      {.v = &layouts[0]} },
    { MODKEY,                       XK_f,      setlayout,      {.v = &layouts[1]} },
    { MODKEY,                       XK_m,      setlayout,      {.v = &layouts[2]} },
    { MODKEY,                       XK_space,  setlayout,      {0} },
    { MODKEY|ShiftMask,             XK_space,  togglefloating, {0} },
    { MODKEY,                       XK_0,      view,           {.ui = ~0 } },
    { MODKEY|ShiftMask,             XK_0,      tag,            {.ui = ~0 } },
    TAGKEYS(                        XK_1,                      0)
    TAGKEYS(                        XK_2,                      1)
    TAGKEYS(                        XK_3,                      2)
    TAGKEYS(                        XK_4,                      3)
    TAGKEYS(                        XK_5,                      4)
    TAGKEYS(                        XK_6,                      5)
    TAGKEYS(                        XK_7,                      6)
    TAGKEYS(                        XK_8,                      7)
    TAGKEYS(                        XK_9,                      8)
    { MODKEY|ShiftMask,             XK_q,      quit,           {0} },
};
```

### Building DWM

After customizing `config.h`, rebuild and reinstall DWM to apply changes:

```bash
make clean install
```

**Note:** Ensure that you have the necessary permissions (often `sudo`) to install binaries to system directories.

### Applying Patches

DWM's functionality can be extended through patches provided by the suckless community. Patches modify the source code to introduce new features without requiring a complete overhaul.

**Steps to Apply a Patch:**

1. **Download the Patch:**
   
   Visit the [suckless patches page](https://dwm.suckless.org/patches/) and download the desired patch.

2. **Apply the Patch:**

    ```bash
    patch < path/to/patch.diff
    ```

3. **Rebuild and Install:**

    ```bash
    make clean install
    ```

**Common Patches:**

- **statuscolors:** Adds color support to the status bar.
- **swallow:** Automatically manages terminal windows as child clients.
- **fancybar:** Enhances the status bar with additional information and aesthetics.

**Note:** Always read the patch documentation and ensure compatibility with your DWM version before applying.

---

## Advanced Features

### Status Bar

DWM includes a simple status bar at the top or bottom of the screen, displaying information like the current time, system status, and active tags.

**Customization:**

Modify the `setstatus` function in `config.h` to change the status bar's appearance and content.

**Example:**

```c
/* function to set the window title */
void
settitle(const Arg *arg)
{
    if (!arg->v)
        return;
    strncpy(stext, (const char *)arg->v, sizeof(stext) - 1);
    stext[sizeof(stext) - 1] = '\0';
    drawbar(selmon);
}
```

### Multi-Monitor Support

DWM natively supports multiple monitors (referred to as "monitors" or "tags" on different screens). Users can manage windows across monitors seamlessly using key bindings.

**Key Bindings:**

Switch focus between monitors using `Mod + [hjkl]` or specific key combinations defined in `config.h`.

### Scripting and Automation

While DWM does not have built-in scripting capabilities, users can automate tasks by leveraging external scripts and key bindings.

**Example: Launch Applications**

Define key bindings in `config.h` to launch frequently used applications.

```c
static const char *browsercmd[]  = { "firefox", NULL };
{ MODKEY,                       XK_b,      spawn,          {.v = browsercmd } },
```

### Patching for Enhanced Functionality

By applying community patches, users can introduce advanced features such as:

- **Resizable Master Area:** Allows dynamic resizing of the master window.
- **Scratchpads:** Temporary hidden windows for quick access.
- **Gapless Grid:** Enhances window tiling with gapless layouts.

---

## Resources

- **Official DWM Website:** [https://dwm.suckless.org/](https://dwm.suckless.org/)
- **DWM GitHub Repository:** [https://git.suckless.org/dwm](https://git.suckless.org/dwm)
- **DWM Source Code:** [https://git.suckless.org/dwm/tree/config.def.h](https://git.suckless.org/dwm/tree/config.def.h)
- **DWM Patches:** [https://dwm.suckless.org/patches/](https://dwm.suckless.org/patches/)
- **Suckless Wiki:** [https://suckless.org/](https://suckless.org/)
- **DWM Discussion Forum:** [https://suckless.org/forum/](https://suckless.org/forum/)
- **Books and Guides:**
    - *DWM: The Dynamic Window Manager* by [Author Name] (Hypothetical)
    - *Mastering DWM* by [Author Name] (Hypothetical)

---
