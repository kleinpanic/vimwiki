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

| **Key**      | **Description**                                        |
|--------------|--------------------------------------------------------|
| `q`          | `Record Macro`                                         |
| `r`          | `reload`                                               |
| `R`          | `reload (Bypass cache)`                                |
| `t`          | `toggle`                                               |
| `tsh`        | `Toggle scripts for the current host (Temporary)`      |
| `tSh`        | `tsh but permanently.`                                 |
| `tsH/tsu`    | `like tshb ut including subdomains / with exexact URL` |
| `tph`        | `Toggle plugins`                                       |
| `T`          | `Tab-focus`                                            |
| `yd`         | `Yank Domain`                                          |
| `ym`         | `Yank inline [{title}]({url})`                         |
| `yp`         | `yank pretty-url`                                      |
| `yt`         | `yank title`                                           |
| `yy`         | `yank`                                                 |
| `yD`         | `yank domain -s`                                       |
| `yM`         | `yank inline [{title}]({url}) -s`                      |
| `yP`         | `yank pretty-url -s`                                   |
| `yT`         | `yank title -s`                                        |
| `yY`         | `yank -s`                                              |
| `u`          | `undo closing tab`                                     |
| `U`          | `Undo something                                        |
| `i`          | `enter insert-mode`                                    |
| `o`          | `Open`                                                 |
| `O`          | `Open in a new tab (open -t)`                          |
| `go`         | `edit & open current url`                              |
| `gO`         | `like go, in new tab`                                  |
| `xO`         | `Like go, in bg. tab`                                  |
| `xo`         | `Open in background tab`                               |
| `wo`         | `open in new window`                                   |
| `ad`         | `Cancel download`                                      |
| `sf`         | `Save config`                                          |
| `ss`         | `set config`                                           |
| `sk`         | `set bind key`                                         |
| `sl`         | `set config in new tab`                                |
| `Ss`         | `Show settings`                                        |
| `Sb`         | `bookmark-list --jump`                                 |
| `Sh`         | `history`                                              |
| `Sq`         | `bookmark list`                                        |
| `pp`         | `Open url from clipboard`                              |
| `pP`         | `Open url from selection`                              |
| `Pp`         | `pp in new tab`                                        |
| `PP`         | `pP in new tap`                                        |
| `wp`         | `pp in new window`                                     |
| `wP`         | `pP in new window`                                     |
| `d`          | `close tab and open right tab`                         |
| `D`          | `close tab and open left tab`                          |
| `F`          | `Follow hints in new tab`                              |
| `f`          | `Follow hints in current tab`                          |
| `wf`         | `Follow hint in new window`                            |
| `G`          | `Scroll to bottom`                                     |
| `gg`         | `Scroll to top`                                        |
| `g$`         | `tab focus -1`                                         |
| `g0`         | `tab focus 1 `                                         |
| `ga`         | `open -t`                                              |
| `gb`         | `bookmark-load`                                        |
| `gd`         | `download`                                             |
| `gf`         | `view source`                                          |
| `gi`         | `hint inputs`                                          |
| `gm`         | `tab-move`                                             |
| `gt`         | `tab-select`                                           |
| `gu`         | `navigate up`                                          |
| `g^`         | `tab-focus 1`                                          |
| `gB`         | `bookmark-load in new tab`                             |
| `gC`         | `tab-clone`                                            |
| `gD`         | `tab-give`                                             |
| `gJ`         | `tab move +`                                           |
| `gK`         | `tab-move -`                                           |
| `gU`         | `Navigate up -t`                                       |
| `h`          | `scroll left`                                          |
| `H`          | `Go back`                                              |
| `th`         | `Back in a new tab`                                    |
| `wh`         | `Back in a new window`                                 |
| `tl`         | `Forward in a new tab`                                 |
| `wl`         | `Forward in a new window`                              |
| `J`          | `Next Tab`                                             |
| `j`          | `scroll down`                                          |
| `K`          | `Previous tab`                                         |
| `k`          | `Scroll up`                                            |
| `L`          | `Forward`                                              |
| `l`          | `Scroll right`                                         |
| `cd`         | `download-clear`                                       |
| `ce`         | `config-edit`                                          |
| `co`         | `tab-only`                                             |
| `cs`         | `config-source`                                        |
| `v`          | `Viual mode`                                           |
| `B`          | `Load quickmark`                                       |
| `b`          | `load quick-mark`                                      |
| `wb`         | `load quick-mark in new window`                        |
| `N`          | `Search prev`                                          |
| `n`          | `Search next`                                          |
| `M`          | `Save Book-mark`                                       |
| `m`          | `Save quickmark`                                       |
| `.`          | `Repeat command`                                       |
| `/`          | `Search`                                               |
| `?`          | `Search backwards`                                     |
| `,`          | `jump to scroll mark`                                  |
| `:`          | `command mode`                                         |
| `;`          | `ext. hitns`                                           |
| `;b`         | `open hint in background tab`                          |
| `;f`         | `open hint in foreground tab`                          |
| `;h`         | `hover over hint (mouse over)`                         |
| `;i`         | `hint images`                                          |
| `;l`         | `Hint images in new tab`                               |
| `;t`         | `hint inputs`                                          |
| `;o`         | `put hinted url in cmd. line `                         |
| `;O`         | `like ;o but in a new tab`                             |
| `;y`         | `yank hinted url to clipboard`                         |
| `;Y`         | `yabked hinted url to selection`                       |
| `;r`         | `Rapid hinting`                                        |
| `;R`         | `;r in a new window.`                                  |
| `[[`         | `Click "previous"-link on page`                        |
| `]]`         | `clink on "next"-link on page`                         |
| `{{`         | `Like [[ but in new tab`                               |
| `}}`         | `Like ]] but in a new tab.`                            |
| `<Ctrl-A>`   | `Increase no. in URL`                                  |
| `<Ctrl-X>`   | `Decrement no. in URL.`                                |
| `-`          | `Zoom out`                                             |
| `+`          | `Zoom in`                                              |
| `=`          | `Set zoom level to 100`                                |
| ```          | `Set scroll mark`                                      |
| `@`          | `Run macro`                                            |
| `Ctrl-F`     | `Page Down`                                            |
| `Ctrl-B`     | `Page Up`                                              |
| `Ctrl-D`     | `half Page Down`                                       |
| `Ctrl-U`     | `Half Page Up`                                         |
| `Ctrl-Tab`   | `Select prev. tab`                                     |
| `Ctrl-V`     | `Passtrhough mode`                                     |
| `Ctrl-Q`     | `Quit `                                                |
| `Ctrl-H`     | `Home`                                                 |
| `Ctrl-S`     | `Stop loading`                                         |
| `Ctrl-Alt-P` | `Print `                                               |
| `Ctrl-E`     | `Open Editor (Only in insert mode)`                    |
| `Ctrl-P`     | `Prev. history Item (only in command mode)`            |
| `Ctrl-N`     | `Next History Item (Only in command mode)`             |
| `Ctrl-D`     | `Delete Current item (Only in command mode)`           |
| `Alt-Num`    | `Select Tab`                                           |
| `Tab`        | `Cycle completion items`                               |
|--------------|--------------------------------------------------------|

### Command Mode

Accessed by pressing `:` in Normal Mode. Allows execution of various commands.

| **Command**           | Description                                                            |
|-----------------------|------------------------------------------------------------------------|
| `adblock-update`      | `Update block lists for both the host- and the brave ad blocker`       |
| `back`                | `Go back in the history of the current tab`                            |
| `bind`                | `Bind to a key to a command`                                           |
| `bookmark-add`        | `Save the current page as a bookmark or a specific url`                |
| `bookmark-del`        | `Delete a bookmark`                                                    |
| `bookmark-list`       | `Show all bookmarks / quickmarks`                                      |
| `bookmark-load`       | `Load a bookmark`                                                      |
| `clear-keychain`      | `Clear the current entered key chain`                                  |
| `clear-messages`      | `Clear all message notifications`                                      |
| `click-element`       | `Click the element matching the given filter`                          |
| `close`               | `Close the current window`                                             |
| `cmd-edit`            | `Open an editor to modify the current command`                         |
| `cmd-later`           | `Execute a command after some time`                                    |
| `cmd-repeat`          | `Repeat a given command.`                                              |
| `cmd-repeat-last`     | `Repeat the last executed command.`                                    |
| `cmd-run-with-count`  | `Run a command with the given count.`                                  |
| `cmd-set-text`        | `Preset the statusbr to some text`                                     |
| `config-clear`        | `Set all settings back to their default.`                              |
| `config-cycle`        | `Cycle an option between multiple values.`                             |
| `config-dict-add`     | `Add a key / value pair to a dictionary option`                        |
| `config-dict-remove`  | `Remoive a key from a dict`                                            |
| `config-diff`         | `Show all customized options`                                          |
| `config-edit`         | `Open the config.py file in the editor.`                               |
| `config-list-add`     | `Append a value t oa config option that is a list.`                    |
| `config-list-remove`  | `Remove a value from a list.`                                          |
| `config-source`       | `Read a config.py file.`                                               |
| `config-unset`        | `Unset an option.`                                                     |
| `config-write-py`     | `Write the current configuration to a config.py file.`                 |
| `devtools`            | `Toggle the developer tools (Web inspector).`                          |
| `devtools-focus`      | `Toggle focus between the devtools / tab.`                             |
| `download`            | `Download a given URL or current page if no URL given, `               |
| `download-cancel`     | `Cancel the last / [count]th download`                                 |
| `download-clear`      | `Remove all finished downloads from the list.`                         |
| `download-delete`     | `Delete the last / [count]th download.`                                |
| `download-open`       | `Open the last / [count]th download`                                   |
| `download-remove`     | `Remove the last / [count]th download from the list. `                 |
| `download-retry`      | `Retry the first failed / [count]th download. `                        |
| `edit-text`           | `Open an external editor with the current selected form field. `       |
| `edit-url`            | `Navigate to a rl formed in an external editor. `                      |
| `fake-key`            | `Send a fake keypress or key string to the website or qutebrowser. `   |
| `forward`             | `Go forward in the history of the current tab. `                       |
| `fullscreen`          | `Toggle fullscreen mode. `                                             |
| `greasemonkey-reload` | `Re-read greasemonkey script from disk.`                               |
| `help`                | `Show help about a command or setting. `                               |
| 'hint'                | `start hinting`                                                        |
| `hisgtory`            | `Show browsing history`                                                |
| `history-clear`       | `Clear all browsing history.`                                          |
| `home`                | `Open main startpage in current tab.`                                  |
| `insert-text`         | `Insert text at cursor position.`                                      |
| `jseval`              | `Evaluate a JavaScript string. `                                       |
| `jump-mark`           | `Jump to the mark named by key`                                        |
| `macro-record`        | `Start or stop recording a macro. `                                    |
| `macro-run`           | `Run a recorded macro`                                                 |
| `message-error`       | `Show an error message in the statusbar`                               |
| `message-info`        | `Show an info message in the status bar `                              |
| `message-warning`     | `Show a warning message in the status bar.`                            |
| `messages`            | `Show a log of past messages`                                          |
| `mode-enter`          | `Enter a key mode.`                                                    |
| `navigate`            | `open typical prev/next links or navigate using the url path.`         |
| `nop`                 | `Do nothing.`                                                          |
| `open`                | `Openm a URL in the current / [count]th tab.`                          |
| `print`               | `Print the current / [count]th tab.`                                   |
| `process`             | `Manage processes spawned by qutebrowser`                              |
| `quickmark-add`       | `Add a new quickmark`                                                  |
| `quickmark-del`       | `Delete a quickmark`                                                   |
| `quickmark-load`      | `Load a quickmark`                                                     |
| `quickmark-save`      | `Save the current page as a quickmark`                                 |
| `quit`                | `Quit quitebrowser.`                                                   |
| `reload`              | `Reload the current / [count]th tab.`                                  |
| `report`              | `Report a bug in quitebrowser.`                                        |
| `restart`             | `Restart qutebrowser while keeping existing tabs open.`                |
| `save`                | `Save configs and state.`                                              |
| `screenshot`          | `Take a screenshot of the current shown part of the page. `            |
| `scroll`              | `Scroll the current tab in the given direction.`                       |
| `scroll-page`         | `Scroll the frame page-wise`                                           |
| `scroll-px`           | `Scroll the current tab by count * dx/dy pixels.`                      |
| `scroll-to-anchor`    | `Scroll to the given anchor in the document. `                         |
| `scoll-to-perc`       | `Scroll to a specific percentage of the page. `                        |
| `search`              | `Search for a text on the current page. With no text, clear results.`  |
| `search-next`         | `Continue the search to the ([current]th) next term.`                  |
| `search-prev`         | `Continue the search to the ([count]th) previous term.`                |
| `selection-follow`    | `Follow the selected text. `                                           |
| `sesson-delete`       | `Delete a session. `                                                   |
| `session-load`        | `Load a session.`                                                      |
| `session-save`        | `Save a session.`                                                      |
| `set`                 | `Set an option`                                                        |
| `set-mark`            | `Set a mark at the current scroll position in the current tab.`        |
| `spawn`               | `Spawn an external command`                                            |
| `stop`                | `Stop loading in the current / [count]th tab.`                         |
| `tab-clone`           | `Duplicate the current tab.`                                           |
| `tab-close`           | `Cloe the current / [count]th tab.`                                    |
| `tab-focus`           | `Select the tab given as argument / [count]/`                          |
| `tab-give`            | `Give the current tab to a new or existing window if win_id is given.` |
| `tab-move`            | `move the current tab according to the argument and [count].`          |
| `tab-mute`            | `Mute / Unmut the current / [count]th tab.`                            |
| `tab-next`            | `Switch to the next tab, or switch [count] tabs forward.`              |
| `tab-only`            | `Close all tabs except for the current one. `                          |
| `tab-pin`             | `Pin / Unpin the current / [count]th tab.`                             |
| `tab-prev`            | `Switch to the previous tab or switch [count] tabs back.`              |
| `tab-select`          | `Select tab by index or url / title best match. `                      |
| `tab-take`            | `Take a tab from another window. `                                     |
| `unbind`              | `Unbind a keychain.`                                                   |
| `undo`                | `Re-open the last closed tab(s) or window. `                           |
| `version`             | `Show version information`                                             |
| `view-source`         | `Show the source of the current page in a new tab.`                    |
| `window-only`         | `Close all windows except for the current one. `                       |
| `yank`                | `Yank (copy) something to the clipboard or primary selection.`         |
| `zoom`                | `Select the zooom level for the current tab.`                          |
| `zoom-in`             | `Increase the zoom level for the current tab. `                        |
| `zoom-out`            | `Decrease the zoom level for the current tab.`                         |
|-----------------------|------------------------------------------------------------------------|

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

## Setting Reference 

### Setting Table 

| Settings                                        | Descriptions |
|-------------------------------------------------|--------------|
| `alias`                                         |              |
| `auto_save.interval`                            |              |
| `auto_save.session`                             |              |
| `backend`                                       |              |
| `bindings.commands`                             |              |
| `bindings.default`                              |              |
| `bindgings.key_mappings`                        |              |
| `changelo_after_upgrade`                        |              |
| `colors.completion.categroy.bg`                 |              |
| `colors.completion.category.border.bottom`      |              |
| `colors.completion.category.border.top`         |              |
| `colors.completion.category.fg`                 |              |
| `colors.completion.even.bg`                     |              |
| `colors.completion.fg`                          |              |
| `colorscompletion.item.selected.bg`             |              |
| `colors.completion.item.selected.border.bottom` |              |
| `colors.completion.item.selected.boarder.top`   |              |
| `colors.completion.item.selected.fg`            |              |
| `colors.completion.item.selected.match.fg`      |              |
| `colors.completion.match.fg`                    |              |
| `colors.completion.odd.bg`                      |              |
| `colors.completion.scrollbar.bg`                |              |
| `colors.completion.scrollbar.fg`                |              |
| `colors.contextmenu.disabled.bg`                |              |
| `colors.contextmenu.disabled.fg`                |              |
| `colors.contextmenu.menu.bg`                    |              |
| `colors.contextmenu.menu.fg`                    |              |
| `colors.contextmenu.selected.bg`                |              |
| `color.contextmenu.selected.fg`                 |              |
| `colors.downloads.bar.bg`                       |              |
| `colors.downloads.error.bg`                     |              |
| `colors.downloads.error.fg`                     |              |
| `colors.downloads.start.bg`                     |              |
| `colors.downloads.start.fg`                     |              |
| `colors.downloads.stop.bg`                      |              |
| `colors.downloads.stop.fg`                      |              |
| `colors.downloads.system.bg`                    |              |
| `colors.downloads.system.fg`                    |              |
| `colors.hints.bg`                               |              |
| `colors.hints.fg`                               |              |
| `colors.hints.match.fg`                         |              |
| `colors.keyhint.bg`                             |              |
| `colors.keyhint.fg`                             |              |
| `colors.keyhint.suffix.fg`                      |              |
| `colors.messages.error.bg`                      |              |
| `colors.messages.error.border`                  |              |
| `colors.messages.error.fg`                      |              |
| `colors.messages.info.bg`                       |              |
| `colors.messages.info.border`                   |              |
| `colors.messages.info.fg`                       |              |
| `colors.messages.warning.bg`                    |              |
| `colors.prompts.bg`                             |              |
| `colors.prompts.border`                         |              |
| `colors.prompts.fg`                             |              |
| `colors.prompts.selected.bg`                    |              |
| `colors.prompts.selected.fg`                    |              |
| `colors.statusbar.caret.bg`                     |              |
| `colors.statusbar.caret.fg`                     |              |
| `colors.statusbar.caret.selection.bg`           |              |
| `colors.statusbar.caret.selection.fg`           |              |
| `colors.statusbar.command.fg`                   |              |
| `colors.statusbar.command.private.bg`           |              |
| `colors.statusbar.command.private.fg`           |              |
| `colors.statusbar.insert.bg`                    |              |
| `colors.statusbar.normal.bg`                    |              |
| `colors.statusbar.normal.fg`                    |              |
| `colors.statusbar.passthrough.bg`               |              |
| `colors.statusbar.passthrough.fg`               |              |
| `colors.statusbar.private.bg`                   |              |
| `colors.statusbar.private.fg`                   |              |
| `colors.statusbar.progress.bg`                  |              |
| `colors.statusbar.url.error.fg`                 |              |
| `colors.statusbar.url.fg`                       |              |
| `colors.statusbar.url.hover.fg`                 |              |
| `colors.statusbar.url.warn.fg`                  |              |
| `colors.tabs.bar.bg`                            |              |
| `colors.tabs.even.bg`                           |              |
| `colors.tabs.even.fg`                           |              |
| `colors.tabs.indicator.error`                   |              |
| `colors.tabs.indicator.start`                   |              |
| `colors.tabs.indicator.stop`                    |              |
| `colors.tabs.indicator.system`                  |              |
| `colors.tabs.odd.bg`                            |              |
| `colors.tabs.odd.fg`                            |              |
| `colors.tabs.pinned.even.bg`                    |              |
| `colors.tabs.pinned.even.fg`                    |              |
| `colors.tabs.pinned.odd.bg`                     |              |
| `colors.tabs.pinned.odd.fg`                     |              |
| `colors.tabs.pinned.selected.even.bg`           |              |
| `colors.tabs.pinned.selected.even.fg`           |              |
| `colors.tabs.pinned.selected.odd.bg`            |              |
| `colors.tabs.pinned.selected.odd.fg`            |              |
| `colors.tabs.selected.even.bg`                  |              |
| `colors.tabs.selected.even.fg`                  |              |
| `colors.tabs.selected.odd.bg`                   |              |
| `colors.tabs.selected.odd.fg`                   |              |
| `colors.tooltip.fg`                             |              |
| `colors.webpage.bg`                             |              |
| `colors.webpage.darkmode.algorithm`             |              |
| `colors.webpage.darkmode.contrast`              |              |
| `colors.webpage.darkmode.enabled`               |              |
| `colors.webpage.darkmode.policy.images`         |              |
| `colors.webpage.darkmode.policy.page`           |              |
| `colors.webpage.darkmode.threshold.background`  |              |
| `colors.webpage.darkmode.threshold.foreground`  |              |
| `colors.webpage.preffered_color_scheme`         |              |
| `completion.cmd_history_max_items`              |              |
| `completion.delay`                              |              |
| `completion.favorite_paths`                     |              |
| `completion.height`                             |              |
| `completion.min_chars`                          |              |
| `completion.open_categories`                    |              |
| `completion.quick`                              |              |
| `completion.scrollbar.width`                    |              |
| `completion.show`                               |              |
| `completion.shrink`                             |              |
| `completion.timestamp_format`                   |              |
| `completion.use_best_match`                     |              |
| `completion.web_history.exclude`                |              |
| `completion.web_history.max_items`              |              |
| `confirm_quit`                                  |              |
| `content.autoplay`                              |              |
| `content.blocking.adblock.lists`                |              |
| `content.blocking.enabled`                      |              |
| `content.blocking.hosts.block_subdomains`       |              |
| `content.blocking.hosts.lists`                  |              |
| `content.blocking.method`                       |              |
| `content.blocking.whitelist`                    |              |
| `content.cache.appcache`                        |              |
| `content.cache.maximum_pages`                   |              |
| `content.cache.size`                            |              |
| `content.canvas_reading`                        |              |
| `content.cookies.store`                         |              |
| `content.default_encoding`                      |              |
| `content.desktop_capture`                       |              |
| `content.dns_prefetch`                          |              |
| `content.frame_flattening`                      |              |
| `content.fullscreen,overlay_timeout`            |              |
| `content.fullscreen.window`                     |              |
| `content.geolocation`                           |              |
| `content.headers.accept_language`               |              |
| `content.headers.custom`                        |              |
| `content.headers.do_not_track`                  |              |
| `content.headers.user_agent`                    |              |
| `content.hyperlink_auditing`                    |              |
|                                                 |              |








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

