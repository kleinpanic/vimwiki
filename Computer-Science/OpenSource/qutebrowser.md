# Qutebrowser

## Overview

**Qutebrowser** is a keyboard-focused, minimalistic web browser with a strong emphasis on user customization and efficiency. Inspired by the modal editing of Vim, Qutebrowser allows users to navigate the web entirely through the keyboard, minimizing the need for a mouse. It leverages modern web technologies and offers extensive configuration options, making it a powerful tool for users who prefer a streamlined and programmable browsing experience.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Basic Concepts](#basic-concepts)
4. [Getting Started](#getting-started)
    - [Launching Qutebrowser](#launching-qutebrowser)
    - [Basic Navigation](#basic-navigation)
5. [Features](#features)
    - [Vim-like Keybindings](#vim-like-keybindings)
    - [Extensive Customization](#extensive-customization)
    - [Ad Blocking and Privacy](#ad-blocking-and-privacy)
    - [Command Line Interface](#command-line-interface)
    - [Session Management](#session-management)
6. [Comprehensive Key Bindings](#comprehensive-key-bindings)
    - [Normal Mode](#normal-mode)
    - [Insert Mode](#insert-mode)
    - [Caret Mode](#caret-mode)
    - [Command Mode](#command-mode)
    - [Hint Mode](#hint-mode)
    - [Bindings for Specific Actions](#bindings-for-specific-actions)
7. [Customization and Configuration](#customization-and-configuration)
    - [Configuration File](#configuration-file)
    - [Setting Options](#setting-options)
    - [Custom Key Bindings](#custom-key-bindings)
8. [Advanced Features](#advanced-features)
    - [Userscripts and Extensions](#userscripts-and-extensions)
    - [Autoconfig](#autoconfig)
    - [Scripting with Python](#scripting-with-python)
9. [Tips and Best Practices](#tips-and-best-practices)
10. [Resources](#resources)
11. [Conclusion](#conclusion)

---

## Introduction

Qutebrowser is designed for users who prefer to navigate the web using the keyboard rather than the mouse. Its minimalist interface reduces distractions, allowing users to focus on content. By adopting a modal approach similar to Vim, Qutebrowser provides a highly efficient browsing experience once the keybindings are mastered. It supports modern web standards and offers features like ad blocking, customizable keybindings, and extensive configuration through a straightforward configuration file.

---

## Installation

### On Linux

**Using Package Managers:**

- **Arch Linux:**
  
  ```bash
  sudo pacman -S qutebrowser
  ```

- **Debian/Ubuntu:**
  
  ```bash
  sudo apt update
  sudo apt install qutebrowser
  ```

- **Fedora:**
  
  ```bash
  sudo dnf install qutebrowser
  ```

**Using pip:**

Ensure you have Python and pip installed.

```bash
pip install qutebrowser
```

### On macOS

**Using Homebrew:**

```bash
brew install qutebrowser
```

### On Windows

Qutebrowser is primarily developed for Unix-like systems. However, it can be installed on Windows using the Windows Subsystem for Linux (WSL).

1. **Install WSL:** Follow Microsoft's [installation guide](https://docs.microsoft.com/en-us/windows/wsl/install).

2. **Install Qutebrowser within WSL:**

    ```bash
    sudo apt update
    sudo apt install qutebrowser
    ```

**Note:** Ensure you have an X server running on Windows to display GUI applications from WSL.

---

## Basic Concepts

- **Modes:** Qutebrowser operates in different modes, primarily Normal, Insert, and Command modes, akin to Vim.
- **Keybindings:** Central to Qutebrowser's efficiency, allowing for navigation, control, and execution of commands without leaving the keyboard.
- **Hints:** Contextual identifiers that let users interact with page elements quickly.
- **Tabs and Windows:** Organize browsing sessions effectively with multiple tabs and windows.

---

## Getting Started

### Launching Qutebrowser

Simply run:

```bash
qutebrowser
```

Or, to open a specific URL:

```bash
qutebrowser https://www.example.com
```

### Basic Navigation

- **Open a New Tab:** `:open https://www.example.com` or press `:`
- **Close Current Tab:** `:tab-close` or press `:`
- **Switch Between Tabs:** Use keybindings (refer to the Key Bindings section)

---

## Features

### Vim-like Keybindings

Embracing the modal editing philosophy, Qutebrowser allows users to navigate and control the browser using familiar Vim keybindings, promoting efficiency and speed.

### Extensive Customization

Users can tailor Qutebrowser to their preferences through a configuration file (`~/.config/qutebrowser/config.py`), modifying everything from keybindings to appearance.

### Ad Blocking and Privacy

Built-in ad blocking features enhance privacy and browsing speed. Users can customize filter lists and control cookie behaviors.

### Command Line Interface

Qutebrowser offers a powerful command-line interface, enabling users to perform actions and configure settings directly from the terminal.

### Session Management

Save and restore browsing sessions, ensuring continuity across browsing sessions.

---

## Comprehensive Key Bindings

Qutebrowser's keybindings are categorized based on the mode they operate in. Below is a detailed list of default keybindings for each mode.

### Prefix Key

- **Default Prefix:** `Ctrl + a` (can be customized)
- **Example Usage:** Press `Ctrl + a` followed by a command key to execute actions.

### Normal Mode

The primary mode for navigation and control. Similar to Vim's normal mode.

| **Key**        | **Description**                                         |
|----------------|---------------------------------------------------------|
| `h`            | Move left                                               |
| `j`            | Move down                                               |
| `k`            | Move up                                                 |
| `l`            | Move right                                              |
| `gg`           | Go to top of the page                                   |
| `G`            | Go to bottom of the page                                |
| `H`            | Go to top of the visible page                           |
| `M`            | Go to middle of the visible page                        |
| `L`            | Go to bottom of the visible page                        |
| `0`            | Go to start of the line                                 |
| `$`            | Go to end of the line                                   |
| `d`            | Scroll down half a page                                 |
| `u`            | Scroll up half a page                                   |
| `D`            | Scroll down one page                                    |
| `U`            | Scroll up one page                                      |
| `f`            | Open file dialog                                        |
| `b`            | Go back in history                                      |
| `r`            | Reload the page                                         |
| `R`            | Force reload the page                                   |
| `t`            | Open a new tab                                          |
| `T`            | Open a new tab in the background                        |
| `x`            | Close the current tab                                    |
| `c`            | Close the current tab                                    |
| `w`            | Open window switcher                                     |
| `W`            | Close the current window                                 |
| `n`            | Next tab                                                |
| `p`            | Previous tab                                            |
| `P`            | Switch to the previous tab                               |
| `:`            | Open command prompt                                     |
| `;`            | Cycle through hints                                      |
| `.`            | Execute the last command                                 |
| `/`            | Start a search                                           |
| `?`            | Start a reverse search                                   |
| `y`            | Yank (copy) the current URL                              |
| `Y`            | Yank (copy) all URLs in the current tab                 |
| `v`            | Enter caret mode (visual selection)                      |
| `V`            | Enter insert mode                                        |
| `b`            | Navigate back in history                                 |
| `gU`           | Change the current URL to uppercase                     |
| `gu`           | Change the current URL to lowercase                     |
| `guu`          | Change the current URL to lowercase and yank            |
| `gUU`          | Change the current URL to uppercase and yank            |
| `zx`           | Reload and update all cached information                 |
| `zi`           | Toggle zoom                                               |
| `ZQ`           | Quit without saving                                      |
| `ZZ`           | Save and quit                                            |

### Insert Mode

Used for typing text into input fields or forms.

| **Key**        | **Description**                                         |
|----------------|---------------------------------------------------------|
| `Esc`          | Return to normal mode                                   |
| `Ctrl + c`     | Return to normal mode                                   |
| `Ctrl + [`     | Return to normal mode                                   |
| `i`            | Enter insert mode before the cursor                     |
| `a`            | Enter insert mode after the cursor                      |
| `I`            | Enter insert mode at the beginning of the line           |
| `A`            | Enter insert mode at the end of the line                 |
| `o`            | Open a new line below and enter insert mode              |
| `O`            | Open a new line above and enter insert mode              |

### Caret Mode

Allows navigation and selection within the webpage's text.

| **Key**        | **Description**                                         |
|----------------|---------------------------------------------------------|
| `j`            | Move caret down                                         |
| `k`            | Move caret up                                           |
| `h`            | Move caret left                                         |
| `l`            | Move caret right                                        |
| `0`            | Move caret to the start of the line                     |
| `$`            | Move caret to the end of the line                       |
| `w`            | Move caret to the start of the next word                 |
| `b`            | Move caret to the start of the previous word             |
| `e`            | Move caret to the end of the current word               |
| `v`            | Start visual selection                                   |
| `V`            | Start line-wise visual selection                        |
| `Ctrl + v`     | Start block-wise visual selection                       |
| `y`            | Yank (copy) the selected text                            |
| `d`            | Delete the selected text                                 |
| `c`            | Change the selected text                                 |
| `Esc`          | Exit caret mode                                          |

### Command Mode

Accessed by pressing `:` in Normal Mode. Allows execution of various commands.

| **Command**        | **Description**                                         |
|--------------------|---------------------------------------------------------|
| `:open <url>`      | Open a new URL in the current tab                        |
| `:tab-open <url>`  | Open a new URL in a new tab                               |
| `:tab-close`       | Close the current tab                                     |
| `:tab-next`        | Switch to the next tab                                    |
| `:tab-prev`        | Switch to the previous tab                                |
| `:quit`            | Quit Qutebrowser                                         |
| `:quit-all`        | Quit all tabs and exit                                    |
| `:restart`         | Restart Qutebrowser                                      |
| `:config-write`    | Save the current configuration to the config file         |
| `:config-source`   | Reload the configuration from the config file             |
| `:hint links`      | Enter hint mode to follow links                           |
| `:hint images`     | Enter hint mode to open images                             |
| `:hint all`        | Enter hint mode for all elements                           |
| `:download`        | Start a download for the selected link                     |
| `:buffer <number>` | Switch to the specified buffer by number                   |
| `:spawn <command>` | Execute an external command                                |
| `:bookmark-add <name>` | Add a bookmark with the specified name                |
| `:bookmark-load <name>` | Load the bookmark with the specified name           |
| `:session-save <name>` | Save the current session with the specified name     |
| `:session-load <name>` | Load the saved session with the specified name      |
| `:help`            | Open the help documentation                                |

### Hint Mode

Facilitates interaction with specific elements on the webpage using hints.

| **Key**        | **Description**                                         |
|----------------|---------------------------------------------------------|
| `f`            | Open a link in the current tab                           |
| `F`            | Open a link in a new tab                                 |
| `;f`           | Open a link in the current tab using a regex hint         |
| `;F`           | Open a link in a new tab using a regex hint               |
| `y`            | Yank the URL of the hinted element                        |
| `d`            | Download the hinted element's URL                         |
| `c`            | Change the hint mode to select a different element        |
| `Esc`          | Exit hint mode                                            |

### Bindings for Specific Actions

| **Key Combination** | **Description**                                         |
|---------------------|---------------------------------------------------------|
| `Shift + J`         | Scroll down one line                                    |
| `Shift + K`         | Scroll up one line                                      |
| `Ctrl + d`          | Scroll down half a page                                 |
| `Ctrl + u`          | Scroll up half a page                                   |
| `Ctrl + f`          | Scroll down one page                                    |
| `Ctrl + b`          | Scroll up one page                                      |
| `g`                 | Go to top of the page                                   |
| `G`                 | Go to bottom of the page                                |
| `b`                 | Go back in history                                      |
| `r`                 | Reload the current page                                 |
| `R`                 | Force reload the current page                           |
| `m`                 | Add a bookmark                                           |
| `b` then `m`        | Add a bookmark with the selected name                   |
| `p`                 | Paste from clipboard                                     |
| `yy`                | Yank the current URL                                     |
| `Y`                 | Yank all URLs in the current tab                        |
| `ZQ`                | Quit without saving                                     |
| `ZZ`                | Save and quit                                            |
| `~`                 | Toggle hint mode                                         |
| `:open`             | Open a new URL                                           |
| `:spawn`            | Execute an external command                              |

---

## Comprehensive Key Bindings

Below is a detailed list of all default Qutebrowser key bindings. These bindings are categorized based on the mode they operate in: Normal, Insert, Caret, Command, and Hint modes.

### Normal Mode

The primary mode for navigation and control. Similar to Vim's normal mode.

| **Key**         | **Description**                                         |
|-----------------|---------------------------------------------------------|
| `h`             | Move left                                               |
| `j`             | Move down                                               |
| `k`             | Move up                                                 |
| `l`             | Move right                                              |
| `gg`            | Go to top of the page                                   |
| `G`             | Go to bottom of the page                                |
| `H`             | Go to top of the visible page                           |
| `M`             | Go to middle of the visible page                        |
| `L`             | Go to bottom of the visible page                        |
| `0`             | Go to start of the line                                 |
| `$`             | Go to end of the line                                   |
| `d`             | Scroll down half a page                                 |
| `u`             | Scroll up half a page                                   |
| `D`             | Scroll down one page                                    |
| `U`             | Scroll up one page                                      |
| `f`             | Open file dialog                                        |
| `b`             | Go back in history                                      |
| `r`             | Reload the page                                         |
| `R`             | Force reload the page                                   |
| `t`             | Open a new tab                                          |
| `T`             | Open a new tab in the background                        |
| `x`             | Close the current tab                                   |
| `c`             | Close the current tab                                   |
| `w`             | Open window switcher                                     |
| `W`             | Close the current window                                |
| `n`             | Next tab                                                |
| `p`             | Previous tab                                            |
| `P`             | Switch to the previous tab                               |
| `:`             | Open command prompt                                     |
| `;`             | Cycle through hints                                      |
| `.`             | Execute the last command                                 |
| `/`             | Start a search                                           |
| `?`             | Start a reverse search                                   |
| `y`             | Yank (copy) the current URL                              |
| `Y`             | Yank (copy) all URLs in the current tab                 |
| `v`             | Enter caret mode (visual selection)                      |
| `V`             | Enter insert mode                                        |
| `b`             | Navigate back in history                                 |
| `gU`            | Change the current URL to uppercase                     |
| `gu`            | Change the current URL to lowercase                     |
| `guu`           | Change the current URL to lowercase and yank            |
| `gUU`           | Change the current URL to uppercase and yank            |
| `zx`            | Reload and update all cached information                 |
| `zi`            | Toggle zoom                                               |
| `ZQ`            | Quit without saving                                      |
| `ZZ`            | Save and quit                                            |
| `Ctrl + a`      | Select all text                                          |
| `Ctrl + r`      | Reload the current page                                  |
| `Ctrl + p`      | Open the command prompt                                  |
| `Ctrl + f`      | Open a search bar for forward search                     |
| `Ctrl + b`      | Open a search bar for backward search                    |
| `Ctrl + h`      | Open history                                              |
| `Ctrl + m`      | Show media elements (images, videos)                      |

### Insert Mode

Used for typing text into input fields or forms.

| **Key**         | **Description**                                         |
|-----------------|---------------------------------------------------------|
| `Esc`           | Return to normal mode                                   |
| `Ctrl + c`      | Return to normal mode                                   |
| `Ctrl + [`      | Return to normal mode                                   |
| `i`             | Enter insert mode before the cursor                      |
| `a`             | Enter insert mode after the cursor                       |
| `I`             | Enter insert mode at the beginning of the line            |
| `A`             | Enter insert mode at the end of the line                  |
| `o`             | Open a new line below and enter insert mode               |
| `O`             | Open a new line above and enter insert mode               |

### Caret Mode

Allows navigation and selection within the webpage's text.

| **Key**         | **Description**                                         |
|-----------------|---------------------------------------------------------|
| `j`             | Move caret down                                         |
| `k`             | Move caret up                                           |
| `h`             | Move caret left                                         |
| `l`             | Move caret right                                        |
| `0`             | Move caret to the start of the line                     |
| `$`             | Move caret to the end of the line                       |
| `w`             | Move caret to the start of the next word                 |
| `b`             | Move caret to the start of the previous word             |
| `e`             | Move caret to the end of the current word               |
| `v`             | Start visual selection                                   |
| `V`             | Start line-wise visual selection                        |
| `Ctrl + v`      | Start block-wise visual selection                       |
| `y`             | Yank (copy) the selected text                            |
| `d`             | Delete the selected text                                 |
| `c`             | Change the selected text                                 |
| `Esc`           | Exit caret mode                                          |

### Command Mode

Accessed by pressing `:` in Normal Mode. Allows execution of various commands.

| **Command**           | **Description**                                         |
|-----------------------|---------------------------------------------------------|
| `:open <url>`         | Open a new URL in the current tab                       |
| `:tab-open <url>`     | Open a new URL in a new tab                              |
| `:tab-close`          | Close the current tab                                    |
| `:tab-next`           | Switch to the next tab                                   |
| `:tab-prev`           | Switch to the previous tab                               |
| `:quit`               | Quit Qutebrowser                                        |
| `:quit-all`           | Quit all tabs and exit                                   |
| `:restart`            | Restart Qutebrowser                                     |
| `:config-write`       | Save the current configuration to the config file        |
| `:config-source`      | Reload the configuration from the config file            |
| `:hint links`         | Enter hint mode to follow links                          |
| `:hint images`        | Enter hint mode to open images                            |
| `:hint all`           | Enter hint mode for all elements                          |
| `:download`           | Start a download for the selected link                    |
| `:buffer <number>`    | Switch to the specified buffer by number                  |
| `:spawn <command>`    | Execute an external command                               |
| `:bookmark-add <name>`| Add a bookmark with the specified name                    |
| `:bookmark-load <name>`| Load the bookmark with the specified name                |
| `:session-save <name>`| Save the current session with the specified name          |
| `:session-load <name>`| Load the saved session with the specified name           |
| `:help`               | Open the help documentation                               |

### Hint Mode

Facilitates interaction with specific elements on the webpage using hints.

| **Key**         | **Description**                                         |
|-----------------|---------------------------------------------------------|
| `f`             | Open a link in the current tab                           |
| `F`             | Open a link in a new tab                                 |
| `;f`            | Open a link in the current tab using a regex hint         |
| `;F`            | Open a link in a new tab using a regex hint               |
| `y`             | Yank the URL of the hinted element                        |
| `d`             | Download the hinted element's URL                         |
| `c`             | Change the hint mode to select a different element        |
| `Esc`           | Exit hint mode                                            |

### Bindings for Specific Actions

| **Key Combination** | **Description**                                         |
|---------------------|---------------------------------------------------------|
| `Shift + J`         | Scroll down one line                                    |
| `Shift + K`         | Scroll up one line                                      |
| `Ctrl + d`          | Scroll down half a page                                 |
| `Ctrl + u`          | Scroll up half a page                                   |
| `Ctrl + f`          | Scroll down one page                                    |
| `Ctrl + b`          | Scroll up one page                                      |
| `g`                 | Go to top of the page                                   |
| `G`                 | Go to bottom of the page                                |
| `b`                 | Go back in history                                      |
| `r`                 | Reload the current page                                 |
| `R`                 | Force reload the current page                           |
| `m`                 | Add a bookmark                                           |
| `y`                 | Yank the current URL                                     |
| `Y`                 | Yank all URLs in the current tab                        |
| `ZQ`                | Quit without saving                                     |
| `ZZ`                | Save and quit                                            |
| `~`                 | Toggle hint mode                                         |
| `:`                 | Open a new URL                                           |
| `:spawn`            | Execute an external command                              |

---

## Customization and Configuration

Qutebrowser is highly customizable through its configuration file, allowing users to tailor the browser to their specific needs and preferences.

### Configuration File

Located at `~/.config/qutebrowser/config.py`, the configuration file allows users to set options, define key bindings, and customize behavior.

**Example `config.py`:**

```python
# Import the config object
config.load_autoconfig(False)

# Set the default search engine
c.url.searchengines = {
    'DEFAULT': 'https://www.google.com/search?q={}',
    'ddg': 'https://duckduckgo.com/?q={}',
    'wiki': 'https://en.wikipedia.org/wiki/Special:Search?search={}'
}

# Set the start page
c.url.start_pages = ['https://www.example.com']

# Enable dark mode
c.colors.webpage.darkmode.enabled = True

# Customize fonts
c.fonts.default_family = 'Fira Code'
c.fonts.default_size = '12pt'

# Enable smooth scrolling
c.scrolling.smooth = True

# Set the zoom level
c.zoom.default = '100%'

# Set content settings
c.content.javascript.enabled = True
c.content.images = True
c.content.autoplay = False

# Enable dark mode for web content
c.colors.webpage.darkmode.enabled = True
```

### Setting Options

Users can set various options to control the behavior and appearance of Qutebrowser.

**Example: Disable Autoplay Videos**

```python
c.content.autoplay = False
```

**Example: Enable JavaScript**

```python
c.content.javascript.enabled = True
```

### Custom Key Bindings

Users can redefine existing key bindings or create new ones to enhance their browsing experience.

**Example: Change the Prefix Key to `Ctrl + a`**

```python
# Unbind the default prefix
config.bind('<Ctrl-a>', 'nop')

# Set a new prefix
config.bind('<Ctrl-a>', 'mode-enter normal')
```

**Example: Map `Ctrl + t` to Open a New Tab**

```python
config.bind('<Ctrl-t>', 'open -t')
```

**Example: Create a Custom Key Binding to Reload the Page**

```python
config.bind('<Ctrl-r>', 'reload')
```

**Example: Bind `Ctrl + s` to Save the Page**

```python
config.bind('<Ctrl-s>', 'spawn --userscript qute-save')
```

---

## Advanced Features

### Userscripts and Extensions

Qutebrowser supports userscripts and extensions to extend its functionality. Userscripts are external scripts that can be executed within Qutebrowser to perform custom actions.

**Installing Userscripts:**

1. **Create a Userscripts Directory:**

    ```bash
    mkdir -p ~/.local/share/qutebrowser/userscripts
    ```

2. **Add Userscripts:**

    Place executable scripts in the `userscripts` directory. Ensure they have the appropriate shebang (e.g., `#!/usr/bin/env python3`).

3. **Run Userscripts:**

    Invoke userscripts using key bindings or command mode.

**Example: Save Page as PDF Userscript**

```python
#!/usr/bin/env python3
import sys
import subprocess

url = sys.argv[1]
filename = url.split('//')[-1].replace('/', '_') + '.pdf'
subprocess.run(['wkhtmltopdf', url, filename])
```

### Autoconfig

Qutebrowser can automatically generate a configuration file based on user interactions. This feature can be enabled or disabled in the configuration.

**Enable Autoconfig:**

```python
config.load_autoconfig(True)
```

### Scripting with Python

Qutebrowser exposes a Python API for advanced users to create extensions and automate tasks.

**Example: Create a Simple Extension**

1. **Create the Extension Directory:**

    ```bash
    mkdir -p ~/.local/share/qutebrowser/extensions/my_extension
    ```

2. **Create `__init__.py`:**

    ```python
    # ~/.local/share/qutebrowser/extensions/my_extension/__init__.py

    def cmd_show_message(cmd, args, extra):
        cmd.api.status.message('Hello from my_extension!')

    def register_commands(reg):
        reg.register('show-message', cmd_show_message)
    ```

3. **Enable the Extension:**

    Add the following to `config.py`:

    ```python
    config.bind('<Ctrl-m>', 'extension-my_extension:show-message')
    ```

4. **Use the Extension:**

    Press `Ctrl + m` to display the message.

### Plugins

While Qutebrowser doesn't support plugins in the traditional sense, users can leverage userscripts and the Python API to extend its functionality significantly.

---

## Tips and Best Practices

- **Master Keybindings:** Investing time in learning Qutebrowser's keybindings will significantly enhance your browsing efficiency.
- **Customize Your Configuration:** Tailor the `config.py` to suit your workflow, adjusting options and keybindings as needed.
- **Use Userscripts:** Extend Qutebrowser's capabilities by integrating userscripts for repetitive tasks.
- **Leverage Search Engines:** Define multiple search engines for quick access to different search providers.
- **Manage Sessions:** Use session management commands to save and restore your browsing sessions seamlessly.
- **Stay Updated:** Regularly update Qutebrowser to benefit from the latest features and security patches.
- **Backup Configuration:** Keep your `config.py` under version control (e.g., using Git) to track changes and facilitate migrations.

---

## Resources

- **Official Qutebrowser Website:** [https://www.qutebrowser.org/](https://www.qutebrowser.org/)
- **Qutebrowser Documentation:** [https://qutebrowser.org/doc/](https://qutebrowser.org/doc/)
- **Qutebrowser GitHub Repository:** [https://github.com/qutebrowser/qutebrowser](https://github.com/qutebrowser/qutebrowser)
- **Qutebrowser Userscripts Repository:** [https://github.com/qutebrowser/qutebrowser/wiki/Userscripts](https://github.com/qutebrowser/qutebrowser/wiki/Userscripts)
- **Qutebrowser Discussion Forum:** [https://discourse.qutebrowser.org/](https://discourse.qutebrowser.org/)
- **Books and Guides:**
    - *Mastering Qutebrowser* by Jane Doe (Hypothetical)
    - *Keyboard-Focused Browsing with Qutebrowser* by John Smith (Hypothetical)

---

