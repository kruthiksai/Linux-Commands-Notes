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

- #### Key System Files

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

- `top`: It provides a dynamic, real-time view of running processes. It updates the list of processes and their CPU and memory utilization at a regular interval (default is every 3 seconds).

- `kill -9 <PSID>`: Forcefully terminates the process.



### Network Debugging Commands

- `ping <destination>`: The command will send packets to the destination and wait for a response to check network connectivity.
  - `<destination>` can be an IP address (e.g., 8.8.8.8) or a domain name (e.g., google.com).

- `traceroute <destination>`: The command is a network diagnostic tool used to trace the route packets take from your machine to a target destination (such as a website or server). It helps identify network latency, routing issues, and where packets might be getting dropped.
  - `<destination>` can be an IP address (e.g., 8.8.8.8) or a domain name (e.g., google.com).

- `telnet <hostname or IP> <port>`: The telnet command is a network protocol and command-line tool used to establish a connection to a remote server over port 23 (default) or any other specified port. It allows users to interact with remote services manually, making it useful for testing network connectivity, open ports, and server responses.
  - `<destination>` can be an IP address (e.g., 8.8.8.8) or a domain name (e.g., google.com).

- `dig [options] [domain]`: This command is a powerful DNS lookup tool used to query Domain Name System (DNS) servers. It retrieves information about domain names, such as IP addresses, name servers, mail servers, and more.
  - `[domain]` → The domain name or IP address you want to query.
  - `A` → IPv4 address
  - `AAAA` → IPv6 address
  - `MX` → Mail Exchange (Email) servers
  - `NS` → Name Servers
  - `CNAME` → Canonical Name (alias)

### Storage Management Commands

- `ip addr`: This command is used in Linux to display and manage network interfaces and their assigned IP addresses. It is part of the ip command suite (iproute2 package) and is a modern replacement for the older ifconfig command.

- `lsblk`: The command is used to list information about block devices, such as hard drives, SSDs, USB drives, and partitions. It provides a tree-like view of storage devices and their mount points.

- `df`: This command will display the amount of disk space used and available on all mounted filesystems.
- `df -h`: The -h option makes the output more readable by converting the values into human-friendly formats (e.g., KB, MB, GB).
- `df -T`: The -T option includes the type of each file system.

- `file -s /dev/<Newly added Volume>`: This command is used to check the type of data or file system present on a newly attached volume (disk/partition) in Linux.
  - `/dev/xvdb: data`
    - The volume has no file system (raw disk).
    - You need to format the volume before mounting it.

- `mkfs -t <filesystem_type> /dev/<device-name>`: The mkfs (make filesystem) command is used in Linux to format a block device (disk or partition) with a specified file system type.
  - It prepares a disk or partition for data storage by creating a new file system.
  - Warning: Running mkfs on a device erases all data on it!
  - `<filesystem_type>`: Specify file system type (ext4, xfs, ntfs, etc.).
  - `<device-name>`: Block device (e.g., /dev/sdb1).

- `mount /dev/<device-name> <mount-point>`: The mount command is used to attach a storage device (disk, partition, or remote file system) to a directory in the Linux file system, making it accessible for use.
  - `/dev/<device-name>` → The disk or partition you want to mount.
  - `<mount-point>` → The directory where the device will be mounted.

- #### Configuration Files

  - `/etc/mtab`: This file in Linux is a system file that contains information about currently mounted file systems. It serves as a snapshot of all mounted devices and their mount options at a given moment.
  
  - `/etc/fstab` (File System Table): This is a system configuration file that defines how file systems and storage devices should be automatically mounted at boot time. It ensures that disks, partitions, and network file systems are mounted persistently across reboots.
    - Need to copy mount file configuration from mtab to fstab

- `mount -all`: The `mount -a` command mounts all file systems listed in `/etc/fstab` that are not already mounted.
  - It is used to test and apply `/etc/fstab` changes without rebooting.

- `xfs_growfs -d <mount-point>`: This command is used to resize an XFS file system without unmounting it, making it ideal for increasing disk space dynamically.
  - `d` → Expands the file system to use all available space.
  - `<mount-point>` → The directory where the XFS file system is mounted.

### SSH Server Configuration

- `/etc/ssh/sshd_config`: It is the main configuration file for the OpenSSH server (sshd) in Linux. It controls settings related to remote SSH access, authentication, security, and connection policies.
  - After making configuration changes, need to restart ssh:
    - `sudo systemctl restart ssh`

- #### SSH Configuration Parameters
  
  - **Port 22**: SSH listens on this port.
    - Default: `22`
  - **PermitRootLogin no**: Disables direct root login.
    - Default: `yes` (but should be `no`)
  - **PasswordAuthentication yes**: Allows password-based login.
    - Default: `yes`
  - **PubkeyAuthentication yes**: Enables key-based authentication.
    - Default: `yes`
  - **PermitEmptyPasswords no**: Disables empty password login.
    - Default: `no`
  - **AllowUsers user1 user2**: Restricts SSH access to specified users.
    - Default: Not set

### Adding SSH Key to New User

- sudo adduser $NEW_USER # Create the .ssh directory, set ownership and permissions
- sudo mkdir -p /home/$NEW_USER/.ssh
- sudo chmod 700 /home/$NEW_USER/.ssh
- sudo chown $NEW_USER:$NEW_USER /home/$NEW_USER/.ssh # Create the authorized_keys file, set ownership and permissions
- echo "$SSH_PUBLIC_KEY" | sudo tee /home/$NEW_USER/.ssh/authorized_keys > /dev/null
- sudo chmod 600 /home/$NEW_USER/.ssh/authorized_keys
- sudo chown $NEW_USER:$NEW_USER /home/$NEW_USER/.ssh/authorized_keys # Restart SSH service to apply changes
- sudo systemctl restart sshd || sudo systemctl restart ssh || sudo service ssh restart



