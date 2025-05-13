# RHCSA Study Journey: Week 2

This week, I focused on getting more comfortable with **basic Linux command syntax**, directory navigation, file permissions, and package management.
---
## Basic Commands & Navigation

```bash
ls                # Lists files and directories in the current location
ls Documents      # Lists the contents of the 'Documents' directory
ls -l             # Long format: shows permissions, ownership, size, and modification time
ls -r             # Lists files in reverse alphabetical order
ls -l -r          # Combines long format with reverse sorting
pwd               # Prints the current working directory

Note: Linux is case-sensitive. Typing LS instead of ls will return an error like “Permission denied” if the path doesn’t exist.

cd Documents                        # Navigates to the Documents directory
sysadmin@localhost:~/Documents$ 

cd School/Art                       # Navigates to the Art directory inside School
sysadmin@localhost:~/Documents/School/Art$ 

pwd                                 # Confirms current directory
cd ..                               # Goes up one level (to 'School')
cd ~                                # Returns to the user's home directory

ls -l /var/log                      # Lists files in the /var/log directory
ls -lt /var/log                    # Sorts by timestamp (newest first)
ls -l -S /var/log                  # Sorts by file size
ls -lSr /var/log                   # Sorts by file size, reverse order

-rw-r--r-- 1 root   root  18047 Dec 20 2017 alternatives.log
drwxr-x--- 2 root   adm    4096 Dec 20 2017 apache2
-rw-r----- 1 syslog adm    1346 Oct  2 22:17 auth.log
...

File Type Symbols
Symbol	Type	Description
d	#Directory	A folder containing files
-	#Regular file	Standard files (text, binaries, images, etc.)
l	#Symbolic link	Points to another file
s	#Socket	Used for inter-process communication
p	#Pipe	Also for inter-process communication
b	#Block device	Communicates with hardware (e.g., disk)
c	#Character device	Communicates with hardware (e.g., serial port)

su -          # Switch user (creates a new shell as another user)
sudo command  # Runs a command as another user (usually root) without creating a new shell

sysadmin@localhost:~/Documents$ ls -l hello.sh
-rw-r--r-- 1 sysadmin sysadmin 647 Dec 20 2017 hello.sh

Breakdown:
- → regular file
rw- → owner (read/write)
r-- → group (read only)
r-- → others (read only)

Permission Types:
r – read (can view/copy file contents)
w – write (can modify or delete file contents)
x – execute (run file as a program/script)

Changing File Permissions with chmod
chmod u+x hello.sh          # Adds execute permission to the owner
chmod g-w hello.sh          # Removes write permission from the group
chmod o=r hello.sh          # Sets others to read-only
chmod a+x script.sh         # Adds execute permission for all (user, group, others)

Syntax:
chmod [<SET><ACTION><PERMISSION>] <filename>

Where:
SET: u (user), g (group), o (others), a (all)
ACTION: + (add), - (remove), = (set)
PERMISSIONS: r, w, x

sudo chown root hello.sh    # Changes the owner to root

Viewing File Contents
cat file.txt                # Displays entire file
head file.txt               # Shows the beginning of the file
tail file.txt               # Shows the end of the file
head -n 5 file.txt          # First 5 lines
tail -n 5 file.txt          # Last 5 lines

Moving and Removing Files
mv people.csv Work/                          # Moves people.csv to Work directory
mv *.txt School/                             # Moves all .txt files to School directory
rm linux.txt                                 # Deletes linux.txt

Networking & Package Commands
ip a                          # Shows network configuration (better than ipconfig)
apt-get upgrade               # Updates all installed packages
apt-get purge <package_name> # Deletes all files related to a package
