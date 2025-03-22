# ForgeSetup - Project setup and management tool. 

## General Idea: 

- A program to automate project / program setups for various languages, based on best recognized practices and personal settings set in a config file. 
- It needs to manage git repository initiliztion (configurable), and git list management (used by auto_git_update). Handle gh cli to manage gh repositories from the cli (configurable / flags). 
- Project setup needs to include: 1) directory making with name (add flag for name creation based on description), 2) standardized github files (README.md, LICENSE, .gitignore (templated),) 3) standardized github settings (Branch, remote origin, git or gitea, etc, defined by config file). 4. Standardized git / github actions (git add, commit, push, merge conflict management, gh cli - add flag usage). 5) standardized rules (no spaces or special characters, no duplicates,)

## Specifics? 

- Language Detection Dynamically - Dynamically, via path, via flags, or other means, determine the language of the future project and handle multiple languages (have default templates). 
- Directory creation - Pretty easy, add flag for random project name or a smart project name. Based on the detected language there will be a default template / nested directory template structure with basic needed files, and directories. Add option for a baseless option. 
- Git / Github Setpup - based on configs, do this, and setup linting, formating, etc, have base git additions (above). 
- Git setup - Based on config file, after all the files are made, do an initial add and commit and remote add etc and gh creation etc. 
- Path tracking - determined by config file. After git initialization and git repo is setup the path needs to be tracked. Either 1) stupid way or 2) smart way. 1) will just be recording the static path and 2) will record info in a hidden file. A flag needs to be added so that the program will either 1) ue find on the entire computer to update paths or use the file and their changes to update path. This is for handling name changes, deletions, impromper setups. Also the remote and gh repo name needs to reflect these changes. Add option in config for all of this. Track removals. 
- Templates needed: 
  - all languages (C, C++, C#, Python, Ruby, Java, Js, etc)
  - no language
  - common multi language program templates
  - licence templates
  - man page setups (via flags - post setup)
  - bash completion setups (via flags - post setup) *Remember this is also a management tool.* 
   
## Requirements: 

- Language: C 
- Needs README file for it
- Every option that can be configurable should be configurable thru the configuration file. 
- ForgeSetup is project name. End binary product will be called scaffold. 
- Config file needs to be in standard location this needs to be designed as a system utility so first search in .config/forgesetup or /etc/forgesetup/ and then the dir it was ran it. 
# Future
- interactive mode for interactive management. 
- Handle remote setup with ssh pipes
- GUI or TUI mode 
- Automatic code style enforcement temlates based on configs and flags. 
- Config file editable thru binary. 
