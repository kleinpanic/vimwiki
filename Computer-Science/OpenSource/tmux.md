# Tmux

## Overview

**Tmux** (Terminal Multiplexer) is a powerful command-line tool that allows users to manage multiple terminal sessions within a single window. It enables the creation of multiple panes and windows, session persistence, and easy navigation between different tasks without the need to open multiple terminal instances. Tmux is especially valuable for developers, system administrators, and anyone who frequently works in the terminal.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Basic Concepts](#basic-concepts)
4. [Getting Started](#getting-started)
    - [Starting Tmux](#starting-tmux)
    - [Detaching and Attaching Sessions](#detaching-and-attaching-sessions)
5. [Windows and Panes](#windows-and-panes)
    - [Managing Windows](#managing-windows)
    - [Managing Panes](#managing-panes)
6. [Customization and Configuration](#customization-and-configuration)
    - [Tmux Configuration File](#tmux-configuration-file)
    - [Customizing Key Bindings](#customizing-key-bindings)
7. [Comprehensive Key Bindings](#comprehensive-key-bindings)
    - [Prefix Key](#prefix-key)
    - [Session Management](#session-management)
    - [Window Management](#window-management)
    - [Pane Management](#pane-management)
    - [Navigation](#navigation)
    - [Resizing Panes](#resizing-panes)
    - [Copy Mode](#copy-mode)
    - [Miscellaneous](#miscellaneous)
8. [Advanced Features](#advanced-features)
    - [Scripting and Automation](#scripting-and-automation)
    - [Plugins](#plugins)
9. [Tips and Best Practices](#tips-and-best-practices)
10. [Resources](#resources)

---

## Introduction

Tmux is a terminal multiplexer that allows users to switch easily between several programs in one terminal, detach them (they keep running in the background), and reattach them to a different terminal. This is particularly useful for managing long-running processes, organizing workflows, and maintaining persistent terminal sessions across different machines or network connections.

---

## Installation

### On macOS

```bash
brew install tmux
```

### On Ubuntu/Debian

```bash
sudo apt update
sudo apt install tmux
```

### On Fedora

```bash
sudo dnf install tmux
```

### From Source

1. **Clone the Repository:**

    ```bash
    git clone https://github.com/tmux/tmux.git
    ```

2. **Navigate to the Directory:**

    ```bash
    cd tmux
    ```

3. **Build and Install:**

    ```bash
    ./autogen.sh
    ./configure
    make
    sudo make install
    ```

---

## Basic Concepts

- **Session:** A single tmux instance containing multiple windows. Sessions can be detached and reattached.
- **Window:** A single screen within a session, similar to a tab in a web browser.
- **Pane:** A subdivision of a window, allowing multiple terminal instances within the same window.
- **Prefix Key:** A key combination that signals tmux to interpret the next key as a command.

---

## Getting Started

### Starting Tmux

To start a new tmux session:

```bash
tmux
```

Or, to start a session with a specific name:

```bash
tmux new -s mysession
```

### Detaching and Attaching Sessions

- **Detach from a Session:**

    Press `Prefix` + `d` (usually `Ctrl + b` followed by `d`).

- **List All Sessions:**

    ```bash
    tmux ls
    ```

- **Attach to a Session:**

    ```bash
    tmux attach -t mysession
    ```

---

## Windows and Panes

### Managing Windows

- **Create a New Window:**

    `Prefix` + `c`

- **Switch to the Next Window:**

    `Prefix` + `n`

- **Switch to the Previous Window:**

    `Prefix` + `p`

- **Select a Window by Number:**

    `Prefix` + `<number>`

- **Rename the Current Window:**

    `Prefix` + `,`

- **Close the Current Window:**

    `Prefix` + `&`

### Managing Panes

- **Split Window Horizontally:**

    `Prefix` + `%`

- **Split Window Vertically:**

    `Prefix` + `"`

- **Close the Current Pane:**

    `Prefix` + `x`

- **Navigate Between Panes:**

    `Prefix` + Arrow Keys or `Prefix` + `o`

---

## Customization and Configuration

### Tmux Configuration File

Tmux can be customized extensively using the `.tmux.conf` file located in the user's home directory (`~/.tmux.conf`).

**Example `.tmux.conf`:**

```conf
# Set the prefix to Ctrl + a
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix

# Enable mouse support
set -g mouse on

# Set window and pane index starting at 1
set -g base-index 1
setw -g pane-base-index 1

# Use vim keybindings in copy mode
setw -g mode-keys vi

# Reload configuration with Prefix + r
bind r source-file ~/.tmux.conf \; display "Config Reloaded!"
```

### Customizing Key Bindings

Users can redefine or add new key bindings in the `.tmux.conf` file using the `bind-key` command.

**Example: Changing the Prefix Key to Ctrl + a**

```conf
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix
```

---

## Comprehensive Key Bindings

Tmux key bindings are typically combinations that start with the **Prefix Key** (default `Ctrl + b`). Below is a comprehensive list of default key bindings, categorized for easier reference.

### Prefix Key

- **Default Prefix:** `Ctrl + b`
- **Example:** To send a command, press `Ctrl + b` followed by the desired key.

### Session Management

| **Key Combination**      | **Description**                                       |
|--------------------------|-------------------------------------------------------|
| `Prefix` + `d`           | **Detach**: Detach from the current session.         |
| `Prefix` + `s`           | **Choose Session**: Switch between sessions.          |
| `Prefix` + `(`           | **Previous Session**: Switch to the previous session. |
| `Prefix` + `)`           | **Next Session**: Switch to the next session.         |
| `Prefix` + `:`           | **Command Prompt**: Enter tmux command mode.          |
| `tmux kill-session -t <name>` | **Kill Session**: Terminate a specific session.     |

### Window Management

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `c`           | **Create Window**: Open a new window.                    |
| `Prefix` + `,`           | **Rename Window**: Rename the current window.            |
| `Prefix` + `&`           | **Close Window**: Close the current window.              |
| `Prefix` + `n`           | **Next Window**: Move to the next window.                |
| `Prefix` + `p`           | **Previous Window**: Move to the previous window.        |
| `Prefix` + `<number>`    | **Select Window**: Switch to window by number.            |
| `Prefix` + `w`           | **Choose Window**: Open a list to select a window.        |
| `Prefix` + `f`           | **Find Window**: Search for a window by name.             |
| `Prefix` + `,`           | **Rename Window**: Rename the current window.             |

### Pane Management

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `%`           | **Split Vertically**: Split the current pane vertically. |
| `Prefix` + `"`           | **Split Horizontally**: Split the current pane horizontally. |
| `Prefix` + `x`           | **Close Pane**: Close the current pane.                   |
| `Prefix` + `o`           | **Toggle Pane**: Toggle between panes.                    |
| `Prefix` + `;`           | **Last Pane**: Move to the last active pane.              |
| `Prefix` + Arrow Keys     | **Navigate Panes**: Move to adjacent panes.               |
| `Prefix` + `q`           | **Display Pane Numbers**: Show pane numbers for quick selection. |
| `Prefix` + `Space`       | **Toggle Layout**: Switch between predefined pane layouts. |
| `Prefix` + `{`           | **Move Pane Left**: Swap pane with the pane on the left.  |
| `Prefix` + `}`           | **Move Pane Right**: Swap pane with the pane on the right. |

### Navigation

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + Arrow Keys     | **Navigate Windows/Panes**: Move between windows or panes using arrow keys. |
| `Prefix` + `n`           | **Next Window**: Move to the next window.                |
| `Prefix` + `p`           | **Previous Window**: Move to the previous window.        |
| `Prefix` + `l`           | **Last Window**: Move to the last active window.         |
| `Prefix` + `t`           | **Show Clock**: Display a clock in the status bar.        |
| `Prefix` + `g`           | **Goto Line**: Jump to a specific line (if enabled).      |

### Resizing Panes

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `Ctrl + Arrow Keys` | **Resize Pane**: Adjust the size of the current pane in the direction of the arrow key pressed. |
| `Prefix` + `Alt + Arrow Keys` | **Alternative Resize**: Another method to resize panes, depending on configuration. |

### Copy Mode

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `[`           | **Enter Copy Mode**: Start copying text.                 |
| `Prefix` + `]`           | **Paste Buffer**: Paste the copied text.                 |
| `Prefix` + `Ctrl + b`    | **Begin Selection**: Start selecting text in copy mode.  |
| `Prefix` + `Space`       | **Start Selection**: Begin text selection in copy mode.  |
| `Prefix` + `Enter`       | **Copy Selection**: Copy the selected text to the buffer. |
| `Prefix` + `y`           | **Yank Selection**: Yank (copy) the selected text.        |

### Miscellaneous

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `?`           | **List Key Bindings**: Show a list of all key bindings.   |
| `Prefix` + `d`           | **Detach Session**: Detach from the current session.      |
| `Prefix` + `z`           | **Toggle Zoom**: Maximize or restore the current pane.    |
| `Prefix` + `c`           | **Create Window**: Open a new window.                     |
| `Prefix` + `:`           | **Command Prompt**: Enter tmux command mode for advanced commands. |

### Control Keys

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `&`           | **Kill Window**: Close the current window.               |
| `Prefix` + `,`           | **Rename Window**: Rename the current window.            |
| `Prefix` + `f`           | **Find Window**: Search for a window by name.             |
| `Prefix` + `n`           | **Next Window**: Move to the next window.                |
| `Prefix` + `p`           | **Previous Window**: Move to the previous window.        |
| `Prefix` + `w`           | **Choose Window**: Open a window selection menu.          |
| `Prefix` + `s`           | **Choose Session**: Switch between sessions.             |

---

## Comprehensive Key Bindings

Below is a detailed list of all default tmux key bindings. These bindings are initiated by the **Prefix Key** (default `Ctrl + b`). Understanding these bindings will enhance your ability to navigate and manage tmux sessions efficiently.

### Prefix Key

- **Default Prefix:** `Ctrl + b`
- **Changing Prefix:** Modify the prefix in `.tmux.conf` using `set-option -g prefix <key>`

### Session Management

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `d`           | **Detach**: Detach from the current session.             |
| `Prefix` + `s`           | **Choose Session**: Switch between existing sessions.    |
| `Prefix` + `(`           | **Previous Session**: Switch to the previous session.     |
| `Prefix` + `)`           | **Next Session**: Switch to the next session.             |
| `Prefix` + `:`           | **Command Prompt**: Enter tmux command mode.              |
| `tmux kill-session -t <name>` | **Kill Session**: Terminate a specific session.     |

### Window Management

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `c`           | **Create Window**: Open a new window.                     |
| `Prefix` + `,`           | **Rename Window**: Rename the current window.             |
| `Prefix` + `&`           | **Close Window**: Close the current window.               |
| `Prefix` + `n`           | **Next Window**: Move to the next window.                 |
| `Prefix` + `p`           | **Previous Window**: Move to the previous window.         |
| `Prefix` + `<number>`    | **Select Window**: Switch to window by number.            |
| `Prefix` + `w`           | **Choose Window**: Open a list to select a window.        |
| `Prefix` + `f`           | **Find Window**: Search for a window by name.             |

### Pane Management

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `%`           | **Split Vertically**: Split the current pane vertically.  |
| `Prefix` + `"`           | **Split Horizontally**: Split the current pane horizontally. |
| `Prefix` + `x`           | **Close Pane**: Close the current pane.                   |
| `Prefix` + `o`           | **Toggle Pane**: Toggle between panes.                    |
| `Prefix` + `;`           | **Last Pane**: Move to the last active pane.              |
| `Prefix` + Arrow Keys     | **Navigate Panes**: Move to adjacent panes using arrow keys. |
| `Prefix` + `q`           | **Display Pane Numbers**: Show pane numbers for quick selection. |
| `Prefix` + `Space`       | **Toggle Layout**: Switch between predefined pane layouts. |
| `Prefix` + `{`           | **Move Pane Left**: Swap pane with the pane on the left.  |
| `Prefix` + `}`           | **Move Pane Right**: Swap pane with the pane on the right. |

### Navigation

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + Arrow Keys     | **Navigate Windows/Panes**: Move between windows or panes using arrow keys. |
| `Prefix` + `n`           | **Next Window**: Move to the next window.                |
| `Prefix` + `p`           | **Previous Window**: Move to the previous window.        |
| `Prefix` + `l`           | **Last Window**: Move to the last active window.         |
| `Prefix` + `t`           | **Show Clock**: Display a clock in the status bar.        |
| `Prefix` + `g`           | **Goto Line**: Jump to a specific line (if enabled).      |

### Resizing Panes

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `Ctrl + Arrow Keys` | **Resize Pane**: Adjust the size of the current pane in the direction of the arrow key pressed. |
| `Prefix` + `Alt + Arrow Keys` | **Alternative Resize**: Another method to resize panes, depending on configuration. |

### Copy Mode

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `[`           | **Enter Copy Mode**: Start copying text.                 |
| `Prefix` + `]`           | **Paste Buffer**: Paste the copied text.                 |
| `Prefix` + `Ctrl + b`    | **Begin Selection**: Start selecting text in copy mode.  |
| `Prefix` + `Space`       | **Start Selection**: Begin text selection in copy mode.  |
| `Prefix` + `Enter`       | **Copy Selection**: Copy the selected text to the buffer. |
| `Prefix` + `y`           | **Yank Selection**: Yank (copy) the selected text.        |

### Miscellaneous

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `?`           | **List Key Bindings**: Show a list of all key bindings.   |
| `Prefix` + `d`           | **Detach Session**: Detach from the current session.      |
| `Prefix` + `z`           | **Toggle Zoom**: Maximize or restore the current pane.    |
| `Prefix` + `c`           | **Create Window**: Open a new window.                     |
| `Prefix` + `:`           | **Command Prompt**: Enter tmux command mode for advanced commands. |

### Control Keys

| **Key Combination**      | **Description**                                           |
|--------------------------|-----------------------------------------------------------|
| `Prefix` + `&`           | **Kill Window**: Close the current window.               |
| `Prefix` + `,`           | **Rename Window**: Rename the current window.            |
| `Prefix` + `f`           | **Find Window**: Search for a window by name.             |
| `Prefix` + `n`           | **Next Window**: Move to the next window.                |
| `Prefix` + `p`           | **Previous Window**: Move to the previous window.        |
| `Prefix` + `w`           | **Choose Window**: Open a window selection menu.          |
| `Prefix` + `s`           | **Choose Session**: Switch between sessions.             |

---

## Advanced Features

### Scripting and Automation

Tmux can be scripted using its command-line interface, allowing for automation of repetitive tasks.

**Example: Creating a New Session with Multiple Windows and Panes**

```bash
tmux new-session -d -s mysession
tmux new-window -t mysession:1 -n 'Editor' 'vim'
tmux new-window -t mysession:2 -n 'Server' 'python -m http.server'
tmux split-window -t mysession:2 -h
tmux attach -t mysession
```

### Plugins

Tmux supports a variety of plugins that enhance its functionality. Popular plugin managers include [Tmux Plugin Manager (TPM)](https://github.com/tmux-plugins/tpm).

**Installing TPM:**

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

**Adding Plugins to `.tmux.conf`:**

```conf
# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'

# Initialize TMUX plugin manager
run '~/.tmux/plugins/tpm/tpm'
```

**Installing Plugins:**

Press `Prefix` + `I` (capital i) to install plugins after reloading `.tmux.conf`.

---

## Tips and Best Practices

- **Consistent Naming:** Name your sessions, windows, and panes descriptively to easily navigate.
- **Use Plugins Wisely:** Enhance tmux functionality with plugins but avoid overloading to maintain performance.
- **Master Copy Mode:** Efficiently navigate and copy text within tmux using copy mode.
- **Customize Key Bindings:** Tailor key bindings to your workflow for increased productivity.
- **Automate Workflows:** Use scripting to set up your development environment quickly.
- **Backup Configuration:** Keep your `.tmux.conf` version-controlled for easy restoration and sharing.

---

## Resources

- **Official Tmux GitHub Repository:** [https://github.com/tmux/tmux](https://github.com/tmux/tmux)
- **Tmux Documentation:** [https://man7.org/linux/man-pages/man1/tmux.1.html](https://man7.org/linux/man-pages/man1/tmux.1.html)
- **Tmux Cheat Sheet:** [https://tmuxcheatsheet.com/](https://tmuxcheatsheet.com/)
- **Tmux Plugin Manager (TPM):** [https://github.com/tmux-plugins/tpm](https://github.com/tmux-plugins/tpm)
- **Awesome Tmux (List of Plugins and Resources):** [https://github.com/rothgar/awesome-tmux](https://github.com/rothgar/awesome-tmux)
- **Books:**
    - *The Tao of tmux* by Tony Narlock
    - *Tmux: Productive Mouse-Free Development* by Brian P. Hogan

---

## Conclusion

Tmux is an indispensable tool for anyone looking to enhance their terminal productivity. With its ability to manage multiple sessions, windows, and panes seamlessly, combined with extensive customization options, tmux empowers users to create efficient and organized workflows. Whether you're a developer, system administrator, or power user, mastering tmux can significantly streamline your command-line experience.

---

