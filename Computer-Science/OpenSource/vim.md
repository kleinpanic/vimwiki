# Vi and Vim and Nvim
## Vi 
- A screen-oriented text editor orignally created for the Unix System. The portable subset of the behavior of vi and programs based on it and the ex editor language supported wit hthese prgrams, is described by the Single Unix Specifications and POSIX.
- Originally the code for vi was written by Bill Joy in 1976, as the visual mode for a line editor called ex that Joy had written with Chuck Haley. Bill Joy's ex 1.1 was released in March 1978. It was not until version 2.0 of ex, released as part of Second BSD in May 1979, that the editor was installed under the name vi (Which took users directly into ex's visual mode), ad the name by which it is known today. Some current implementations of vi can trace their source code ancestry to Bill Joy; and others are completely new. 
- The name "vi" is derived from the shortest unambiguous abbreviation of the ex command visual, which switches the ex line editor to its full-screen mode 
  
### Creation
- vi was derived from a sequence of UNIQ command line editors, starting with ed, which was a line editor designed to work well on teleprinters, rather than display terminal. 
- Ed was enhanced in 1976, making em, which was designed for display termins and was a single-line-at-a-time visual editor. 
- Bill Joy and Chuck Baley, took code from em and ed to make en, and then "extended" en to create ex version 0.1.
- Vi and ex shaire their code; vi is the ex binary launching with the capabilitiy to render the text being edited onto a computer terminal-it is ex's visual mode. The name vi comes from the abbreviated ex command vi to enter visual mode from within it. 
### Interface
- Vi is a modal editor: It operates in either insert mode (where typed text becomes part of the document) or command mode (Where keystrokes are interpreted as commands that control the edit session). 

### VI Key Bindings List

Apologies for any confusion or frustration caused by my previous response. Let's ensure that **all** the keys from your **Complete VI Key Binding List** are thoroughly included and accurately described in the **VI Key Bindings List** table below. I'll cross-verify each key from your list to confirm its presence and description.

---

### 1. VI Key Bindings List

| **Key** | **Description** |
|---------|-----------------|
| **a**   | **Append**: Enter insert mode after the current character. |
| **b**   | **Back Word**: Move the cursor back one word. |
| **c**   | **Change Command**: Delete text and enter insert mode. For example, `cw` changes the current word. |
| **d**   | **Delete Command**: Delete text without entering insert mode. For example, `dw` deletes the current word. |
| **e**   | **End of Word**: Move the cursor to the end of the current word. |
| **f**   | **Find Character**: Find the next occurrence of a character on the current line. For example, `fx` moves the cursor to the next 'x'. |
| **g**   | **Goto Line or Mode**: Typically used in combination with other commands (e.g., `gg` to go to the first line). **UNBOUND** when used alone. |
| **h**   | **Move Left**: Move the cursor one character to the left. |
| **i**   | **Insert**: Enter insert mode before the current character. |
| **j**   | **Move Down**: Move the cursor down one line. |
| **k**   | **Move Up**: Move the cursor up one line. |
| **l**   | **Move Right**: Move the cursor one character to the right. |
| **m**   | **Mark**: Mark the current position with a letter (e.g., `ma` marks the position with 'a'). |
| **n**   | **Next Search**: Repeat the last search in the same direction. |
| **o**   | **Open Line Below**: Open a new line below the current line and enter insert mode. |
| **p**   | **Put**: Paste the text from the buffer after the cursor. |
| **q**   | **Record Macro**: Start or stop recording a macro into a register (e.g., `qa` records a macro to register 'a'). **UNBOUND** when not used for macro recording. |
| **r**   | **Replace**: Replace the character under the cursor with another character. |
| **s**   | **Substitute**: Delete the character under the cursor and enter insert mode. Can also substitute entire lines (e.g., `S`). |
| **t**   | **Till Character**: Move the cursor till just before the specified character on the current line (e.g., `tx`). |
| **u**   | **Undo**: Undo the last change. |
| **v**   | **Visual Mode**: Enter visual mode for selecting text. |
| **w**   | **Next Word**: Move the cursor forward to the beginning of the next word. |
| **x**   | **Delete Character**: Delete the character under the cursor. |
| **y**   | **Yank**: Copy text into the buffer without deleting it. For example, `yw` yanks the current word. |
| **z**   | **Scroll**: Used with other commands to scroll the screen (e.g., `zz` centers the cursor line). |
| **A**   | **Append to Line**: Move to the end of the line and enter insert mode. |
| **B**   | **Back Big Word**: Move the cursor back one "big" word (separated by non-alphanumeric characters). |
| **C**   | **Change to End of Line**: Change text from the cursor to the end of the line and enter insert mode. |
| **D**   | **Delete to End of Line**: Delete text from the cursor to the end of the line. |
| **E**   | **End of Big Word**: Move the cursor to the end of the current "big" word. |
| **F**   | **Find Backward**: Find the previous occurrence of a character on the current line. |
| **G**   | **Goto Line**: Move the cursor to a specific line number or to the end of the file with `G`. |
| **H**   | **Home Line**: Move the cursor to the top of the screen. |
| **I**   | **Insert at Beginning**: Enter insert mode at the beginning of the line. |
| **J**   | **Join Lines**: Join the current line with the next line. |
| **K**   | **Lookup Keyword**: Lookup the keyword under the cursor using the 'keywordprg' option. |
| **L**   | **Last Line**: Move the cursor to the bottom of the screen. |
| **M**   | **Middle Line**: Move the cursor to the middle of the screen. |
| **N**   | **Next Search (Opposite Direction)**: Repeat the last search in the opposite direction. |
| **O**   | **Open Line Above**: Open a new line above the current line and enter insert mode. |
| **P**   | **Put Before**: Paste the text from the buffer before the cursor. |
| **Q**   | **Ex Mode**: Enter Ex mode (legacy feature; often remapped). |
| **R**   | **Replace Mode**: Enter replace mode, where typed characters replace existing ones. |
| **S**   | **Substitute Line**: Delete the entire current line and enter insert mode. |
| **T**   | **Till Backward Character**: Move the cursor till just after the specified character on the current line. |
| **U**   | **Undo All Changes on Line**: Undo all changes made to the current line. |
| **V**   | **Visual Line Mode**: Enter visual line mode for selecting entire lines. |
| **W**   | **Next Big Word**: Move the cursor forward to the beginning of the next "big" word. |
| **X**   | **Delete Character Before**: Delete the character before the cursor. |
| **Y**   | **Yank Line**: Yank (copy) the entire current line. |
| **0**   | **Go to Start of Line**: Move the cursor to the beginning of the current line. |
| **1-9** | **Repeat Commands**: Prefix commands with a number to repeat them multiple times (e.g., `5j` moves down five lines). |
| **!**   | **Filter Through Shell**: Filter selected text through a shell command. In insert mode, insert the current file as a shell command. |
| **@**   | **Execute Macro**: Execute a macro stored in a register (e.g., `@a` runs the macro in register 'a'). |
| **#**   | **Search Backward**: Search backward for the word under the cursor. |
| **$**   | **End of Line**: Move the cursor to the end of the current line. |
| **%**   | **Match Bracket**: Jump to the matching bracket, parenthesis, or brace. |
| **^**   | **First Non-Blank**: Move the cursor to the first non-blank character of the line. |
| **&**   | **Repeat Last Substitute**: Repeat the last substitute (`:s`) command. |
| ***** | **Search for Word Under Cursor**: Search forward for the word under the cursor. |
| **(**   | **Previous Sentence**: Move to the beginning of the previous sentence. |
| **)**   | **Next Sentence**: Move to the beginning of the next sentence. |
| **|**    | **Go to Column**: Move the cursor to a specific column in the current line. Syntax: `|` followed by the column number. |
| **-**    | **Move Down Half Page**: Scroll the window down by half a page. |
| **_**    | **Move to Specific Line**: Similar to `:line`, move to a specific line number. |
| **=**    | **Indent Lines**: Indent the current line or a range of lines. |
| **+**    | **Move Down**: Move the cursor down one line (similar to `j`). |
| **[**    | **Previous Section or Block**: Move to the beginning of the previous section or code block. |
| **]**    | **Next Section or Block**: Move to the beginning of the next section or code block. |
| **{**    | **Previous Paragraph or Block**: Move to the beginning of the previous paragraph or block. |
| **}**    | **Next Paragraph or Block**: Move to the beginning of the next paragraph or block. |
| **;**    | **Repeat Last f, F, t, or T Command**: Repeat the last `f`, `F`, `t`, or `T` command in the same direction. |
| **'**    | **Jump to Mark**: Jump to a previously set mark (e.g., `'a` jumps to mark 'a'). |
| `` ``    | **Jump to Previous Position**: Jump back to the position before the last jump. |
| **:**    | **Enter Command-Line Mode**: Enter Ex command-line mode for extended commands (e.g., `:w`, `:q`). |
| **"**    | **Register Command Prefix**: Specify a register for the next command (e.g., `"aY` yanks to register 'a'). |
| **~**    | **Toggle Case**: Toggle the case of the character under the cursor. |
| **,**    | **Repeat Last f, F, t, or T Command (Reverse)**: Repeat the last `f`, `F`, `t`, or `T` command in the opposite direction. |
| **.**    | **Repeat Last Command**: Repeat the last editing command. |
| **/**    | **Search Forward**: Enter search mode to search forward in the text. |
| **<**    | **Shift Left**: Shift the current line or selected lines to the left (de-indent). |
| **?**    | **Search Backward**: Enter search mode to search backward in the text. |
| **^A**   | **Increment Number**: Increment the number under the cursor. |
| **^B**   | **Scroll Up**: Scroll the window up one full screen. |
| **^C**   | **Interrupt**: Abort the current command or exit insert mode. |
| **^D**   | **Scroll Down**: Scroll the window down half a screen. |
| **^E**   | **Scroll Window Up**: Scroll the window content up without moving the cursor. |
| **^F**   | **Scroll Window Down**: Scroll the window content down without moving the cursor. |
| **^G**   | **Display File Information**: Show information about the file, such as name, position, and status. |
| **^H**   | **Delete Character**: Delete the character before the cursor (similar to backspace). |
| **^I**   | **Insert Tab**: Insert a tab character. |
| **^J**   | **Insert New Line**: Insert a new line (similar to pressing Enter). |
| **^K**   | **Delete to End of Line**: Delete from the cursor to the end of the line. |
| **^L**   | **Redraw Screen**: Redraw the screen, useful if the display gets messed up. |
| **^M**   | **Insert New Line**: Equivalent to ^J; insert a new line. |
| **^N**   | **Next Completion**: In insert mode, cycle to the next completion suggestion. |
| **^O**   | **Temporary Command Mode**: In insert mode, execute one normal mode command and return to insert mode. |
| **^P**   | **Previous Completion**: In insert mode, cycle to the previous completion suggestion. |
| **^Q**   | **Control-V (Insert Literal)**: Insert the next character literally. |
| **^R**   | **Redo**: Redo the last undone change. |
| **^S**   | **Stop (Flow Control)**: Typically freezes the terminal; often requires resetting. |
| **^T**   | **Transpose Characters**: Swap the character before the cursor with the one under it. |
| **^U**   | **Undo All Changes**: Undo all changes made since the last save. |
| **^V**   | **Insert Literal**: Insert the next character literally. |
| **^W**   | **Delete Word**: Delete the word before the cursor. |
| **^X**   | **Cancel Command**: Cancel the current command or operation. |
| **^Y**   | **Scroll Window Up One Line**: Scroll the window content up by one line. |
| **^Z**   | **Suspend Editor**: Suspend Vi and return to the shell. Resume with the `fg` command. |
| **^[**   | **Escape**: Exit to normal mode from insert or other modes. |
| **^\**   | **No Operation**: Typically unbound; can be customized. |
| **^]**   | **Go to Definition**: Jump to the definition of a keyword under the cursor (requires tags). |
| **^^**   | **Jump to Previous File**: Toggle between the current and previous file in the buffer list. |
| **^_**   | **Go to Last Change**: Jump to the position of the last change made. |
| **^?**   | **Backspace**: Equivalent to ^H; delete the character before the cursor. |

---

### Vim Key Bindings List

Vim extends VI's capabilities with additional key bindings and functionalities. Below is a comprehensive list that includes both VI and Vim-specific key bindings.


| Key         | Description |
|-------------|-------------|
| **(All VI Key Bindings)** | *Refer to the VI Key Bindings List above.* |
| **<C-n>**   | **Next Completion**: In insert mode, cycle to the next completion suggestion. |
| **<C-p>**   | **Previous Completion**: In insert mode, cycle to the previous completion suggestion. |
| **<C-o>**   | **Temporary Normal Mode**: Execute one normal mode command and return to insert mode. |
| **<C-w>**   | **Window Management**: Various commands for managing splits and windows (e.g., `<C-w>v` splits vertically). |
| **<C-h>**, **<C-j>**, **<C-k>**, **<C-l>** | **Navigate Windows**: Move between split windows. |
| **<Leader>**| **Leader Key**: Customizable prefix key for user-defined shortcuts. By default, it's `\`. |
| **<Space>** | **Common Leader**: Often set as the leader key for easier access to custom mappings. |
| **<Tab>**   | **Auto Indent/Completion**: Used for auto-indenting lines or triggering completion menus. |
| **<S-Tab>** | **Reverse Auto Indent/Completion**: Reverse the action of `<Tab>`. |
| **:wq**     | **Save and Quit**: Write changes to the file and quit Vim. |
| **:q!**     | **Quit Without Saving**: Quit Vim without saving changes. |
| **:e [file]** | **Edit File**: Open a specified file for editing. |
| **:split** or **:sp** | **Horizontal Split**: Split the window horizontally. |
| **:vsplit** or **:vsp** | **Vertical Split**: Split the window vertically. |
| **:tabnew** | **Open New Tab**: Open a new tab in Vim. |
| **:tabnext** or **:tabn** | **Next Tab**: Move to the next tab. |
| **:tabprev** or **:tabp** | **Previous Tab**: Move to the previous tab. |
| **:buffers** or **:ls** | **List Buffers**: Display a list of open buffers. |
| **:b [n]**  | **Switch Buffer**: Switch to buffer number `n`. |
| **:set number** or **:set nu** | **Show Line Numbers**: Display line numbers in the editor. |
| **:set relativenumber** or **:set rnu** | **Show Relative Line Numbers**: Display relative line numbers. |
| **:syntax on** | **Enable Syntax Highlighting**: Turn on syntax highlighting for supported languages. |
| **:syntax off** | **Disable Syntax Highlighting**: Turn off syntax highlighting. |
| **:set paste** | **Enable Paste Mode**: Disable auto-indenting and other formatting when pasting text. |
| **:set nopaste** | **Disable Paste Mode**: Re-enable auto-indenting and formatting after pasting. |
| **:! [command]** | **Execute Shell Command**: Run a shell command without leaving Vim. |
| **:r ![command]** | **Insert Command Output**: Insert the output of a shell command into the file. |
| **gd**      | **Go to Local Declaration**: Jump to the local declaration of a variable under the cursor. |
| **gD**      | **Go to Global Declaration**: Jump to the global declaration of a variable under the cursor. |
| **gg**      | **Go to First Line**: Move the cursor to the first line of the file. |
| **G**       | **Go to Last Line**: Move the cursor to the last line of the file. |
| **:noh** or **:nohlsearch** | **Clear Search Highlight**: Remove highlighting of search matches. |
| **:set tabstop=4** | **Set Tab Width**: Define the number of spaces a tab character represents. |
| **:set shiftwidth=4** | **Set Indent Width**: Define the number of spaces used for each step of (auto)indent. |
| **:set expandtab** | **Use Spaces Instead of Tabs**: Convert tabs to spaces. |
| **:set noexpandtab** | **Use Tabs**: Retain tab characters. |
| **:set autoindent** | **Enable Auto Indent**: Automatically indent new lines to match the indentation of the previous line. |
| **:set smartindent** | **Enable Smart Indent**: Automatically inserts indentation in some cases. |
| **:set relativenumber** | **Relative Line Numbers**: Show line numbers relative to the current cursor line. |
| **:set cursorline** | **Highlight Current Line**: Highlight the line where the cursor is located. |
| **:set cursorcolumn** | **Highlight Current Column**: Highlight the column where the cursor is located. |
| **:set wrap** | **Enable Line Wrapping**: Wrap long lines onto the next line. |
| **:set nowrap** | **Disable Line Wrapping**: Keep long lines on a single line with horizontal scrolling. |
| **:set spell** | **Enable Spell Checking**: Turn on spell checking. |
| **:set nospell** | **Disable Spell Checking**: Turn off spell checking. |
| **:set list** | **Show Hidden Characters**: Display hidden characters like tabs and end-of-line markers. |
| **:set nolist** | **Hide Hidden Characters**: Conceal hidden characters. |
| **:set ignorecase** | **Ignore Case in Searches**: Make search patterns case-insensitive. |
| **:set smartcase** | **Smart Case Search**: Override `ignorecase` if the search pattern contains uppercase letters. |
| **:set incsearch** | **Incremental Search**: Show search matches as you type. |
| **:set hlsearch** | **Highlight Search Results**: Highlight all matches of the search pattern. |
| **:set noerrorbells** | **Disable Error Bells**: Prevent the terminal from ringing on errors. |
| **:set hidden** | **Enable Hidden Buffers**: Allow switching buffers without saving changes. |
| **:set mouse=a** | **Enable Mouse Support**: Use the mouse for all modes. |
| **:set mouse=nvi** | **Configure Mouse Modes**: Enable mouse support for normal, visual, and insert modes. |

---

### 3. Neovim Key Bindings List

Neovim builds upon Vim's foundation, introducing additional features and improvements. Below is a comprehensive list that includes VI, Vim, and Neovim-specific key bindings.


| Key               | Description |
|-------------------|-------------|
| **(All Vim Key Bindings)** | *Refer to the Vim Key Bindings List above.* |
| **<C-s>**         | **Save File**: Save the current file. Often mapped to `:w`. |
| **<C-q>**         | **Quit Neovim**: Quit Neovim. Often mapped to `:q`. |
| **<C-t>**         | **Open New Tab**: Open a new tab in Neovim. |
| **<C-n>**         | **Open File Explorer**: Open the built-in file explorer (`:NvimTreeToggle` if using NvimTree plugin). |
| **<Leader>ff**    | **Find Files**: Trigger file search (commonly mapped to fuzzy finders like Telescope). |
| **<Leader>fg**    | **Live Grep**: Initiate live grep search across files. |
| **<Leader>fb**    | **Buffers**: List open buffers for quick switching. |
| **<Leader>fh**    | **Help Tags**: Search through help tags. |
| **<Leader>fp**    | **Projects**: Switch between projects. |
| **<C-p>**         | **Telescope Find Files**: Open Telescope's file finder. |
| **<C-f>**         | **Telescope Live Grep**: Open Telescope's live grep search. |
| **<C-b>**         | **Toggle Sidebar**: Open or close the sidebar (e.g., file explorer). |
| **<C-e>**         | **Toggle Terminal**: Open or close the built-in terminal (`:ToggleTerm`). |
| **<C-l>**         | **Reload Configuration**: Reload Neovim's configuration without restarting. |
| **<C-/>**         | **Toggle Comment**: Comment or uncomment selected lines (often mapped via plugins like Commentary or NERDCommenter). |
| **<C-space>**     | **Trigger Completion**: Manually trigger the auto-completion menu. |
| **<C-d>**         | **Toggle Diagnostics**: Show or hide diagnostic messages (requires LSP integration). |
| **<C-]>**         | **Go to Definition**: Jump to the definition of the symbol under the cursor (requires LSP). |
| **<C-k>**         | **Signature Help**: Show function signature help (requires LSP). |
| **<C-j>**         | **Next Diagnostic**: Navigate to the next diagnostic message. |
| **<C-h>**         | **Previous Diagnostic**: Navigate to the previous diagnostic message. |
| **<C-m>**         | **Toggle Markdown Preview**: Open or close Markdown preview (requires plugin). |
| **<F2>**          | **Rename Symbol**: Rename the symbol under the cursor (requires LSP). |
| **<F3>**          | **Format Document**: Automatically format the current document (requires LSP or formatter). |
| **<F4>**          | **Toggle Spell Check**: Enable or disable spell checking. |
| **<F5>**          | **Run Current File**: Execute the current file's code (language-specific). |
| **<F6>**          | **Build Project**: Trigger project build commands (requires build system integration). |
| **<F7>**          | **Toggle Quickfix**: Open or close the quickfix list. |
| **<F8>**          | **Toggle Location List**: Open or close the location list. |
| **<F9>**          | **Run Last Command**: Re-execute the last command or macro. |
| **<F10>**         | **Toggle Git Blame**: Show or hide git blame information (requires git integration). |
| **<F11>**         | **Toggle Git Signs**: Show or hide git change signs in the gutter (requires git integration). |
| **<F12>**         | **Toggle Dashboard**: Open or close the startup/dashboard screen. |
| **<C-\\>**        | **Toggle Terminal Split**: Open or close a terminal split window. |
| **<C-x>**         | **Toggle Explorer**: Open or close the file explorer sidebar (e.g., NvimTree). |
| **<C-v>**         | **Toggle Visual Block Mode**: Enter visual block mode for column-wise selections. |
| **<C-y>**         | **Copy to System Clipboard**: Yank selected text to the system clipboard (often mapped via `"+y`). |
| **<C-p>p**        | **Paste from System Clipboard**: Paste text from the system clipboard (often mapped via `"+p`). |
| **<C-s>**         | **Save All Buffers**: Save all open buffers/files. |
| **<C-z>**         | **Toggle Zen Mode**: Enter or exit distraction-free writing mode (requires plugin). |
| **<C-a>**         | **Select All**: Select all text in the current buffer (often mapped via `ggVG`). |
| **<C-q>**         | **Close Current Buffer**: Close the current buffer without quitting Neovim. |
| **<C-w>w**        | **Switch to Next Window**: Cycle through open split windows. |
| **<C-w>h/j/k/l**  | **Navigate Windows**: Move to the left/down/up/right window respectively. |
| **<C-w>c**        | **Close Window**: Close the current split window. |
| **<C-w>s**        | **Split Window Horizontally**: Split the window into horizontal splits. |
| **<C-w>v**        | **Split Window Vertically**: Split the window into vertical splits. |
| **<C-w>=**        | **Equalize Window Sizes**: Make all split windows equal in size. |
| **<C-w>_**        | **Maximize Window Height**: Maximize the height of the current window. |
| **<C-w>|**        | **Maximize Window Width**: Maximize the width of the current window. |
| **<C-x>o**        | **Close Other Windows**: Close all windows except the current one. |
| **:Neotree toggle** | **Toggle File Explorer**: Open or close Neotree file explorer. |
| **:Telescope find_files** | **Open Telescope File Finder**: Launch Telescope's file finding interface. |
| **:Telescope live_grep** | **Open Telescope Live Grep**: Launch Telescope's live grep search. |
| **:ToggleTerm**   | **Toggle Terminal**: Open or close the built-in terminal. |
| **:LazyGit**      | **Open LazyGit Interface**: Launch the LazyGit interface for Git operations (requires LazyGit integration). |
| **:LspInfo**      | **Show LSP Information**: Display information about active Language Server Protocol clients. |
| **:CocCommand**   | **Execute CoC Command**: Run a command provided by the CoC (Conquer of Completion) plugin. |
| **:NvimTreeToggle** | **Toggle NvimTree**: Open or close the NvimTree file explorer. |
| **:LspStart**     | **Start LSP Server**: Manually start a Language Server Protocol server. |
| **:LspStop**      | **Stop LSP Server**: Manually stop a Language Server Protocol server. |
| **:Mason**        | **Open Mason Installer**: Manage and install LSP servers, DAP servers, linters, and formatters using Mason. |

---
