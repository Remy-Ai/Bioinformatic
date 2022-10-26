---
title: "Chapter2: Linus + Vim + Tmux"
date: 2022-10-26T13:07:32+08:00
lastmod: 2022-10-26T13:07:32+08:00
draft: false
keywords: ['Linux','Vim','Tmux']
description: ""
tags: ['linux']
categories: ['Bioinformatic Series']
author: "Remy Ai"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: false
postMetaInFooter: false
hiddenFromHomePage: true
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: true
mathjaxEnableSingleDollar: true
mathjaxEnableAutoNumber: true

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: true
  options: ""

sequenceDiagrams: 
  enable: true
  options: ""

---
## Basic commands of Linux
- **ls** : list files
    - **ls -l** : list files with details
    - **ls -a** : list all files
    - **ls -al** : list all files with details
    - **ls -lh** : list files with details and size in human readable format
    - **ls -alh** : list all files with details and size in human readable format
- **cd** : change directory
    - **cd ..** : change to parent directory
    - **cd ~** : change to home directory
    - **cd -** : change to previous directory
    - **cd /** : change to root directory
    - **cd *PATH*** : change to PATH directory
- **pwd** : print working directory
    - **pwd -P** : print working directory in physical path
- **mkdir** : make directory
    - **mkdir -p** : make parent directory if not exist
    - **mkdir -m** : make directory with mode
    - **mkdir *NAME*** : make directory with NAME
- **rm** : remove
    - **rm -r** : remove recursively
    - **rm -f** : force remove
    - **rm -rf** : force remove recursively (be serious for this command)
- **rmdir** : remove directory
    - **rmdir -p** : remove parent directory if empty
    - **rmdir *NAME*** : remove directory with NAME
- **touch** : create a file
    - **touch -a** : change access time
    - **touch -m** : change modify time
    - **touch -c** : do not create file
    - **touch -d** : change time
    - **touch -r** : change time to reference file
    - **touch -t** : change time
    - **touch *NAME*** : create a file with NAME
- **cp** : copy
    - **cp -r** : copy recursively
    - **cp -p** : copy with permission
    - **cp -a** : copy recursively with permission
    - **cp -f** : force copy
    - **cp -i** : interactive copy
    - **cp -l** : copy with link
    - **cp -s** : copy with symbolic link
    - **cp -u** : copy with update
    - **cp -v** : copy with verbose
    - **cp *SOURCE* *DESTINATION*** : copy SOURCE to DESTINATION
- **mv** : move
    - **mv -f** : force move
    - **mv -i** : interactive move
    - **mv -u** : move with update
    - **mv -v** : move with verbose
    - **mv *SOURCE* *DESTINATION*** : move SOURCE to DESTINATION
- **cat** : concatenate
  - **cat -n** : concatenate with line number
  - **cat -b** : concatenate with non-empty line number
  - **cat -s** : concatenate with squeeze empty line
- **less** : view file
  - **less -N** : view file with line number
- **head** : view first 10 lines
  - **head -n** : view first n lines
- **tail** : view last 10 lines
  - **tail -n** : view last n lines
- **grep** : search for a pattern
  - **grep -i** : ignore case
  - **grep -v** : invert match
  - **grep -c** : count match
  - **grep -n** : print line number
  - **grep *string*** : print lines with string
- **wc** : word count
  - **wc -l** : count lines
  - **wc -w** : count words
  - **wc -c** : count characters
- **sort** : sort lines of text
  - **sort -r** : reverse sort
  - **sort -n** : sort with number
- **uniq** : report or omit repeated lines  
  - **uniq -c** : count repeated lines
  - **uniq -d** : print only repeated lines
- **cut** : remove sections from each line of files
  - **cut -f** : select fields
  - **cut -d** : use delimiter
  - **cut -c** : select characters
- **paste** : merge lines of files
  - **paste -d** : use delimiter
  - **paste -s** : paste one file at a time
  - **paste - -** : paste two files
- **find** : search for files in a directory hierarchy
  - **find -name** : search for files with name
  - **find -type** : search for files with type
  - **find -size** : search for files with size
- - **find -user** : search for files with user
  - **find -group** : search for files with group
  - **find -perm** : search for files with permission
  - **find -mtime** : search for files with modify time
  - **find -atime** : search for files with access time
  - **find -ctime** : search for files with change time
  - **find -newer** : search for files with newer time
  - **find -empty** : search for empty files
- **which** : locate a command
  - **which -a** : locate all commands
  - **which -s** : locate all commands with status
- **man** : an interface to the system reference manuals
  - **man -k** : search for keyword
  - **man -f** : search for keyword with file
  - **man -w** : search for keyword with path
- **chmod** : change file mode bits
  - **chmod value1+value2+value3 *NAME*** : change file mode bits with value1, value2, value3
    for user, group, other respectively, and NAME is the file name, e.g. chmod 777 *NAME*
    - r: read, use 4
    - w: write, use 2
    - x: execute, use 1
    - -: no permission, use 0
    - **chmod 100 *NAME*** : change file mode bits with user can execute, and NAME is the file name
    - **chmod 600 *NAME*** : change file mode bits with user can read and write, and NAME is the file name
    - **chmod 777 *NAME*** : change file mode bits with user, group, other can read, write and execute, and NAME is the file name
 
- **chown** : change file owner and group
  - **chown user:group *NAME*** : change file owner and group with user and group, and NAME is the file name
  - **chown user *NAME*** : change file owner with user, and NAME is the file name
  - **chown :group *NAME*** : change file group with group, and NAME is the file name
  - **chown . *NAME*** : change file owner and group with current user and group, and NAME is the file name
- **chgrp** : change group ownership
  - **chgrp group *NAME*** : change group ownership with group, and NAME is the file name
  - **chgrp . *NAME*** : change group ownership with current group, and NAME is the file name
  - **chgrp -R group *NAME*** : change group ownership recursively with group, and NAME is the file name
- **ln** : make links between files
  - **ln -s** : make symbolic links
  - **ln -f** : force remove existing destination files
  - **ln -i** : interactive remove existing destination files
  - **ln -v** : verbose remove existing destination files
  - **ln -n** : treat destination that is a symbolic link to a directory as if it were a normal file
  - **ln -b** : remove existing destination files before creating new link
  - **ln -d** : allow the superuser to attempt to hard link directories
- **df** : report file system disk space usage
  - **df -h** : report file system disk space usage with human readable
  - **df -i** : report file system disk space usage with inode
  - **df -k** : report file system disk space usage with kilobyte
  - **df -m** : report file system disk space usage with megabyte
  - **df -l** : report file system disk space usage with local file system
  - **df -s** : report file system disk space usage with summary
- **du** : estimate file space usage
  - **du -h** : estimate file space usage with human readable
  - **du -k** : estimate file space usage with kilobyte
  - **du -m** : estimate file space usage with megabyte
  - **du -s** : estimate file space usage with summary
- **tar** : manipulate tape archives
  - **tar -c** : create a new archive
  - **tar -x** : extract files from an archive
  - **tar -f** : use archive file or device ARCHIVE
  - **tar -v** : verbosely list files processed
  - **tar -z** : filter the archive through gzip
- **gzip** : compress or expand files
  - **gzip -c** : write on standard output, keep original files unchanged
  - **gzip -d** : decompress
  - **gzip -f** : force overwrite of output file and compress links
- **gunzip** : uncompress files
  - **gunzip -c** : write on standard output, keep original files unchanged
  - **gunzip -f** : force overwrite of output file and compress links
- **wget** : non-interactive network downloader
  - **wget -b** : go to background after startup
  - **wget -O** : save to file
  - **wget -c** : continue getting a partially-downloaded file
  - **wget -r** : recursive download
- **curl** : transfer a URL
  - **curl -O** : write output to a file named as the remote file
- **ssh** : OpenSSH SSH client (remote login program)
  - **ssh -p** : connect to the specified port
  - **ssh -l** : connect as the specified user
  - **ssh ip** : connect to the specified ip
- **scp** : secure copy (remote file copy program)
  - **scp -r** : copy directories recursively
  - **scp -P** : connect to the specified port
  - **scp -l** : connect as the specified user
  - **scp ip** : connect to the specified ip

- **top** : display Linux processes
  - **top -b** : batch mode
  - **top -c** : enable colors
  - **top -d** : delay between updates
  - **top -n** : number of iterations
  - **top -p** : show only these processes
  - **top -u** : show only this user's processes
- **ps** : report a snapshot of the current processes
  - **ps -A** : show processes for all users
  - **ps -a** : show processes for all users except session leaders
  - **ps -u** : show processes for the specified user
- **kill** : send a signal to a process
  - **kill -l** : list signal names
  - **kill -s** : specify the name of the signal to be sent
  - **kill -u** : specify the user who owns the process to be signaled
- **killall** : kill processes by name
  - **killall -l** : list signal names
  - **killall -s** : specify the name of the signal to be sent
  - **killall -u** : specify the user who owns the process to be signaledd
- **jobs** : list current jobs
  - **jobs -l** : list current jobs with job IDs
  - **jobs -p** : list current jobs with process IDs
  - **jobs -r** : list current jobs with running jobs
- **awk** : pattern scanning and processing language
- - **awk -F** : set field separator
  - **awk -f** : read program from file
  - **awk -v** : assign value to variable
- **sed** : stream editor for filtering and transforming text
  - **sed -n** : suppress automatic printing of pattern space
  - **sed -e** : add the script to the commands to be executed
  - **sed -f** : add the contents of script-file to the commands to be executed
  - **sed -i** : edit files in place (makes backup if extension supplied)
  - **sed -r** : use extended regular expressions in the script
  - **sed -s** : print only the lines selected by the script
  - **sed -u** : disable all buffering
  - **sed -w** : write the modified buffer into the file

**You can specify the command with your alias in the bash configure file**
***

## Basic commands of Vim
##### open file with vim
    $vim filename 
#### Three mode of vim
  - **command mode** : press ESC to enter command mode
    - `:w` : save file
    - `:q` : quit file
    - `:wq` : save and quit file
    - `:q!` : quit without saving
    - `:wq!` : save and quit without warning
    - `:set nu` : show line number
    - `:set nonu` : hide line number
    - `k` : move cursor up
    - `j` : move cursor down
    - `l` : move cursor right
    - `h` : move cursor left
    - `w` : move cursor to the beginning of next word
    - `b` : move cursor to the beginning of previous word
    - `e` : move cursor to the end of next word
    - `0` : move cursor to the beginning of line
    - `$` : move cursor to the end of line
    - `gg` : move cursor to the beginning of file
    - `G` : move cursor to the end of file
    - `nG` : move cursor to the nth line
    - `dd` : delete current line
    - `ndd` : delete n lines
    - `u` : undo
    - `ctrl+r` : redo
    - `yy` : copy current line
    - `nyy` : copy n lines
    - `p` : paste
    - `x` : delete current character
    - `nx` : delete n characters
    - `r` : replace current character
    - `f` : find next character

  - **visual mode** : press v after enter command mode to enter visual mode
    - `v` : enter visual mode
    - `V` : enter visual line mode
    - `ctrl+v` : enter visual block mode
    - `y` : copy
    - `d` : delete
    - `p` : paste
    - `x` : delete
    - `r` : replace
    - `:` : enter command mode
    - `u` : undo
    - `ctrl+r` : redo
    - `i` : enter insert mode
    - `a` : enter insert mode
    - `o` : enter insert mode
    - `A` : enter insert mode
    - `O` : enter insert mode
    - `ESC` : enter command mode

  - **insert mode** : press i after press `Esc` to enter insert mode
  - **replace mode** : press R after press `Esc` to enter replace mode 

#### you can use `:help` to get more information about vim, and specify the command in your vim configure file

***
## Basic commands of Tmux
- open tmux
    ```
    $tmux
    ```
- open tmux with session name
    ```
    $tmux new -s session_name
    ```
- open tmux with session name and window name
    ```
    $tmux new -s session_name -n window_name
    ```
- open tmux with attach session
    ```
    $tmux attach -t session_name
    ```
- open tmux with attach session and window
    ```
    $tmux attach -t session_name:window_name
    ```
- commands under tmux mode
    - `ctrl+b` : enter tmux mode
    - `ctrl+b d` : detach tmux
    - `ctrl+b c` : create new window
    - `ctrl+b n` : next window
    - `ctrl+b p` : previous window
    - `ctrl+b l` : last window
    - `ctrl+b 0` : window 0
    - `ctrl+b 1` : window 1
    - `ctrl+b 2` : window 2
    - `ctrl+b 3` : window 3
    - `ctrl+b 4` : window 4
    - `ctrl+b 5` : window 5
    - `ctrl+b 6` : window 6
    - `ctrl+b 7` : window 7
    - `ctrl+b 8` : window 8
    - `ctrl+b 9` : window 9
    - `ctrl+b w` : list windows
    - `ctrl+b ,` : rename window
    - `ctrl+b &` : kill window
    - `ctrl+b %` : split window vertically
    - `ctrl+b "` : split window horizontally
    - `ctrl+b o` : next pane
    - `ctrl+b ;` : last pane
    - `ctrl+b q` : show pane numbers
    - `ctrl+b x` : kill pane
    - `ctrl+b z` : toggle pane zoom
    - `ctrl+b [` : enter copy mode
    - `ctrl+b ]` : paste buffer
    - `ctrl+b :` : enter command mode
    - `ctrl+b ?` : list shortcuts
    - `ctrl+b :setw synchronize-panes on` : synchronize panes
    - `ctrl+b :setw synchronize-panes off` : unsynchronize panes
    - `ctrl+b :setw synchronize-panes` : check synchronize-panes status
    - `ctrl+b :setw mouse on` : enable mouse
    - `ctrl+b :setw mouse off` : disable mouse
    - `ctrl+b :setw mouse` : check mouse status
    - `ctrl+b :setw remain-on-exit on` : remain on exit
    - `ctrl+b :setw remain-on-exit off` : not remain on exit
    - `ctrl+b :setw remain-on-exit` : check remain-on-exit status
    - `ctrl+b :setw aggressive-resize on` : aggressive resize

###### you can specify the command in your tmux configure file
