# Linux DevOps Essentials
## Basic navigation commands
* **pwd** - prints current working directory
* **ls** - lists files and directories in current working directory
  - **-a** - option that additionally shows hidden elements
  - **-l** - option that lists files and directories details
* **cd \<path>** - changes working directory to provided one
  - **cd ..** - changes working directory to parent directory
  - **cd \~** - changes working directory to home directory
## Basic file system commands
* **mkdir \<name>** - creates new directory of given name
* **touch \<name>** - creates new file of given name and extension
* **cp \<what_to_copy> \<where_to_copy>** - copies files and directories
  - **cp -r \<what_to_copy> \<where_to_copy>** - copies recursively directories and their contents
* **rm \<path>** - removes files and directories of given name
  - **rm -r \<path>** - removes recursively directories and their contents
* **rmdir \<path>** - removes empty directory
* **mv \<old_location/old_name> \<new_location/new_name>** - moves or renames files or directories
* **find \<path_where_search_starts> -options** - searches files or directories based on given information
  - options include: **-name \<pattern>** - searches by specific name or pattern, **-type \<type>** - searches by type \(e.g. f for files and d for directories\), **-size \<\[+-\]n>** - searches by *n* size as number of characters in file with option + for larger files and - for smaller files, **-mtime \<n>** - searches by modification time where *n* represents days ago
* **cat \<file>** - prints file contents
* **grep \<pattern> \<file>** - searches for patterns in files
  - **grep -r \<pattern> \<file>** - searches recursively in directory and its contents
## Permissions &amp; users
* **chmod \<permissions> \<path>** - changes file or directory permissions, usual use with number representing permissions for 3 user groups - xxx
* **chown \<user\:group> \<path>** - changes file or directory ownership
* **sudo \<command>** - executes command with privileges of superuser
* **useradd / userdel \<username>** - adds or deletes user
* **passwd \<username>** - changes password of given user, if username omitted changes password of logged user
## Process &amp; system management
## Environment variables
## SSH keys management &amp; networking
## Package management
