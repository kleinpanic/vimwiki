
# Comprehensive List of `ls` Command Flags in Linux

The `ls` command in Linux is used to list directory contents. 
Below is a comprehensive list of all the flags available for the `ls` command, along with brief descriptions of what each flag does.

## Basic Usage

ls [options] [file|dir...]

## Flags and Descriptions

- `-a`, `--all`: Show all files, including hidden ones.
- `-A`, `--almost-all`: Show all files except `.` and `..`.
- `--author`: Show the author of each file in long format.
- `-b`, `--escape`: Print C-style escapes for nongraphic characters.
- `--block-size=SIZE`: Use SIZE-byte blocks for file sizes.
- `-B`, `--ignore-backups`: Do not list entries ending with `~`.
- `-c`: Sort by and show ctime (time of last modification of file status).
- `-C`: List entries by columns.
- `--color[=WHEN]`: Colorize the output; WHEN can be `never`, `always`, or `auto`.
- `-d`, `--directory`: List directories themselves, not their contents.
- `-D`, `--dired`: Generate output designed for Emacs' `dired` mode.
- `-f`: Do not sort; enable `-a` and disable `-l`, `-s`.
- `-F`, `--classify`: Append indicator (one of `*/=>@|`) to entries.
- `--file-type`: Append indicator (one of `*=@|`) to entries, but do not append `*`.
- `--format=WORD`: Specify output format; WORD can be one of `across`, `commas`, `horizontal`, `long`, `single-column`, `verbose`, `vertical`.
- `--full-time`: Display full date and time in long format.
- `-g`: Use long listing format without owner information.
- `--group-directories-first`: Group directories before files.
- `-G`, `--no-group`: Do not print group names in long format.
- `-h`, `--human-readable`: Print sizes in human-readable format (e.g., 1K, 234M).
- `--si`: Like `-h`, but use powers of 1000 not 1024.
- `-H`, `--dereference-command-line`: Follow symbolic links listed on the command line.
- `--dereference-command-line-symlink-to-dir`: Follow command line symbolic links that point to directories.
- `--hide=PATTERN`: Do not list entries matching shell PATTERN (overridden by `-a` or `-A`).
- `--hyperlink[=WHEN]`: Hyperlink file names; WHEN can be `never`, `always`, or `auto`.
- `--indicator-style=WORD`: Append indicator with style WORD to entry names; WORD can be `none`, `slash`, `file-type`, `classify`.
- `-i`, `--inode`: Print the index number of each file.
- `-I`, `--ignore=PATTERN`: Do not list entries matching shell PATTERN.
- `-k`, `--kibibytes`: Use 1024-byte blocks for file sizes.
- `-l`: Use a long listing format.
- `-L`, `--dereference`: Show information for the file the symbolic link references.
- `-m`: Fill width with a comma-separated list of entries.
- `-n`, `--numeric-uid-gid`: Like `-l`, but list numeric user and group IDs.
- `-N`, `--literal`: Print entry names without quoting.
- `-o`: Use long listing format without group information.
- `-p`, `--indicator-style=slash`: Append `/` indicator to directories.
- `-q`, `--hide-control-chars`: Print `?` instead of nongraphic characters.
- `--show-control-chars`: Show nongraphic characters as-is (default unless output is a terminal).
- `-Q`, `--quote-name`: Enclose entry names in double quotes.
- `--quoting-style=WORD`: Use quoting style WORD for entry names; WORD can be `literal`, `locale`, `shell`, `shell-always`, `shell-escape`, `shell-escape-always`, `c`, `escape`.
- `-r`, `--reverse`: Reverse order while sorting.
- `-R`, `--recursive`: List subdirectories recursively.
- `-s`, `--size`: Print the allocated size of each file, in blocks.
- `-S`: Sort by file size, largest first.
- `--sort=WORD`: Sort by WORD instead of name; WORD can be `none`, `size`, `time`, `version`, `extension`.
- `--time=WORD`: Select which timestamp to use; WORD can be `atime`, `access`, `use`, `ctime`, `status`, `mtime`, `modification`, `birth`, `creation`.
- `--time-style=STYLE`: Time/date format with `-l`; STYLE can be `full-iso`, `long-iso`, `iso`, `locale`, or `+FORMAT`.
- `-t`: Sort by time, newest first.
- `-T`, `--tabsize=COLS`: Assume tab stops at each COLS instead of 8.
- `-u`: Sort by access time, show access time in long format.
- `-U`: Do not sort; list entries in directory order.
- `-v`: Natural sort of (version) numbers within text.
- `-w`, `--width=COLS`: Set output width to COLS; 0 means no limit.
- `-x`: List entries by lines instead of by columns.
- `-X`: Sort alphabetically by entry extension.
- `-Z`, `--context`: Print any security context of each file.
- `--zero`: End each output line with NUL, not newline.
- `-1`: List one file per line.
- `--help`: Display help and exit.
- `--version`: Output version information and exit.

# References

- [GNU Coreutils ls documentation](https://www.gnu.org/software/coreutils/manual/html_node/ls-invocation.html)
- [Linux man page for ls](https://www.man7.org/linux/man-pages/man1/ls.1.html)
- [Linode: Ls Command in Linux](https://www.linode.com/docs/guides/ls-command/)

