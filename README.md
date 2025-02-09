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


# Additional Linux Commands and System Files

### User and Account Management
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
- `usermod -s /bin/bash <User Name>` : Add login permission to User.
- `passwd <User Name>` : Set a new password to the user.

### Key System Files

- `/etc/passwd` : The /etc/passwd file is one of the key text files that stores user account information, making it accessible to many applications.
  - `username:x:UID:GID:full_name:home_directory:shell`
    - `username`: The user's login name.
    - `x`: Historically, this field contained the user's encrypted password, but now it typically contains an x indicating that the password is stored in /etc/shadow.
    - `UID` (User ID): A unique number assigned to each user.
    - `GID` (Group ID): The primary group ID.
    - `full_name`: Often called the GECOS field, this optional field can store additional user information like the user's real name.
    - `home_directory`: The path to the user's home directory.
    - `shell`: The program that is started every time the user logs into the system; typically a command-line interpreter like /bin/bash.

- `/etc/shadow` : The /etc/shadow file contains the encrypted password data and other related account security information that is critical and sensitive.
  - `username:encrypted_password:last_change:min:max:warn:inactive:expire:reserved`
    - `username`: The user’s login name, matching the entry in /etc/passwd.
    - `encrypted_password`: The user’s hashed password.
    - `last_change`: The date of the last password change, expressed as the number of days since January 1, 1970.
    - `min`: The minimum number of days required between password changes.
    - `max`: The maximum number of days the password is valid.
    - `warn`: The number of days before password expiry that the user is warned.
    - `inactive`: The number of days after a password has expired during which the password can still be changed.
    - `expire`: The absolute date on which the user account is disabled, expressed as the number of days since January 1, 1970.
    - `reserved`: A field reserved for future use.

### System Administration

- `visudo` : Command to edit "/etc/sudoers".

### Process Management

- `ps -ef` : This provides a straightforward, flat list of all processes with detailed information such as the PID, UID, PPID, CPU usage, start time, TTY, and the command that initiated the process.
  - `e`: Show all processes.
  - `f`: Show full format listing.

- `ps faux` : The faux combination produces an output that is easy to read in terms of how processes spawn and relate to each other. It includes the username, CPU and memory usage, and the hierarchical tree of processes.
  - `f`: This option tells ps to display a full-format listing which is more visually comprehensive and includes ASCII art that represents the tree structure of processes.
  - `a`: Show processes for all users.
  - `u`: Display the user/owner of the process along with detailed information such as CPU and memory usage.
  - `x`: Include processes not attached to a terminal.

