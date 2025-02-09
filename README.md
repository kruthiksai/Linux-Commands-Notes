# Linux-Commands-Notes

# Basic Linux Commands

- `cd` : stands for "change directory".
- `cd ..` : Takes you to the previous directory.
- `cd /` : The / symbol represents the root directory, which is the topmost directory in the hierarchy of a filesystem.
- `ls` : List all the files and directories in the current directory.
- `ls -a` : list all the files along with hidden files in the current directory.
- `mkdir <Directory Name>` : Create a Directory.
- `touch <File name>` : Create a file.
- `rm <File name>` : Remove a file.
- `rm -r <Directory Name>` : Remove a Directory.
- `cp <File Name> <Directory Name>` : Copy File.
- `mv <File Name> <Directory Name>` : Move File.
- `pwd` : View the path in which you are currently in.
- `vi <Files>` : Opens editor to modify file content.
  - `:wq` : Save and Quit the File.
  - `:q!` : Quit without saving the content.
  - `i` : Switch to insert mode.
  - `dd` : Delete complete line.
  - `10dd` : Delete 10 lines from the selected line.
  - `dG` : Delete all the lines from the selected line.
  - `u` : undo the changes.
- `whoami` :  The whoami command in Linux is used to display the username of the current user logged into the system.
- `sudo adduser <Username>` : Create a new user.
- `su <Username>` : Switch to created user.
- `chmod 777 <File Name>` : Change User Permission of a File.
  - `7` = 4 (READ) + 2(WRITE)  + 1(EXECUTE).
  - First 7 is for User.
  - Second 7 is for Group.
  - Third 7 is for Others.
- `chown <user-name>:<group-name> <File Name>` : Change owner of the file.
- `usermod -aG <Group Name> <User Name>` : Add User to a new group.
- `usermod -s /sbin/nologin <User Name>` : Remove login permission to user.
