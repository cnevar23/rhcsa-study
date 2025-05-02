# RHCSA Study Journey: Day 1–3

Documenting my hands-on Linux journey as I prepare for the RHCSA (Red Hat Certified System Administrator) exam.

Day 1: Navigation & File Management, Permissions & Ownership and User Management

pwd                      # Print current directory
cd /path                 # Change directory
ls, ls -l, ls -a         # List files (long format, all files)
mkdir dir                # Create directory
mkdir -p parent/child    # Create nested directories
rmdir dir                # Remove empty directory
touch file.txt           # Create empty file
cp file1 file2           # Copy file
mv file file2            # Move or rename file
rm file                  # Remove file
rm -rf dir/              # Remove directory + contents (recursive)
man command              # View manual page
command --help           # Quick help for a command

chmod 755 file           # Set permissions (numeric)
chmod u+x file           # Add execute for user
chmod o-w file           # Remove write for others
chmod a-x file           # Remove execute for all
chmod u=rwx,go= file     # User gets full, group/others none
chown user:group file    # Change file owner and group

whoami                   # Show current user
id                       # Show UID, GID, group memberships
id username              # Show info for specific user
useradd -m user          # Add user with home directory
passwd user              # Set user password
groupadd group           # Create new group
usermod -aG group user   # Add user to group (non-destructive)
userdel user             # Delete user
groupdel group           # Delete group
su - user                # Switch to user with full login shell