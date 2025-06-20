# Linux DevOps Essentials
## If I'll find any other feature to be useful - it'll surely be added!
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
* **chmod \<permissions> \<path>** - changes file or directory permissions, usual use with number representing permissions for 3 user groups (owner, group, rest) - xxx
  - **7** - read, write, execute\
  **6** - read, write\
  **5** - read, execute\
  **4** - read\
  **3** - write, execute\
  **2** - write\
  **1** - execute\
  **0** - none
* **chown \<user\:group> \<path>** - changes file or directory ownership
* **sudo \<command>** - executes command with privileges of superuser
* **useradd / userdel \<username>** - adds or deletes user
* **passwd \<username>** - changes password of given user, if username omitted changes password of logged user
## Process &amp; system management
* **ps** - prints currently running processes
  - **ps aux** - prints details of currently running processes
* **top / htop** - monitors system resources and processes in real time
* **kill \<PID>** - terminates process of given PID
  - **kill -9 \<PID>** - forcefully terminates process of given PID
* **systemctl** - manages system services
  - **systemctl start \<service>** - starts specified service
  - **systemctl stop \<service>** - stops specified service
  - **systemctl status \<service>** - checks status of specified service
* **journalctl** - prints system logs
  - **journalctl -u \<service>** - prints system logs of specified service
* **df -h \<path>** - prints disk usage, if path omitted prints all information
* **du -h \<path>** - estimates files and directories disk usage, if path omitted estimates all files and directories
* **free -h** - prints system memory usage
* **uptime** - prints system uptime and load averages
## Environment variables
* **export \<VARIABLE_NAME=value>** - sets environment variable
* **env** - prints environment variables
* **echo $VARIABLE_NAME** - prints given environment variable
## Networking
* **wget \<URL>** - downloads files from given URL
* **curl \<URL>** - transfers data with given URL
  - **curl -C - \<URL>** - option that resumes download that has been interupted
  - **curl -O \<URL>** - option that downloads file and saves it under addresses name
  - **curl -X \<HTTP_method> -d \<request_data> \<URL>** - option that sends request using given HTTP method, -d option is used to specify data to be sent with request
* **ping \<URL>** - sends ICMP request to given host to test connection
* **nc -v \<host> \<port>** - creates network connections for debbuging and monitoring, -v stands for more detailed output
  - **nc -l \<host> \<port>** - option that creates server on given host and port and listens for connections
  - **nc -z \<host> \<port>** - option that scans for open ports, one \(xxx\), multiple \(xxx xxx\) or range \(xxx-xxx\) ports may be specified
* **netstat** - displays network statistics and connections
  - **netstat -a** - displays all sockets
  - **netstat -t** - displays all TCP ports
  - **netstat -u** - displays all UDP ports
  - **netstat -l** - displays all listeting ports
  - **netstat -s** - displays networking statistics
  - **netstat -r** - displays routing table
  - **netstat -i** - displays interface table
* **ip / ifconfig** - network interface configuration
  - **ip addr** - displays IP addresses associated with all network devices
  - **ip addr show \<interface>** - displays information related to a specific interface
  - **ip link** - displays link layer information, including characteristics of link layer devices currently available
  - **ip route** - displays routing table, showing the route packets your network will take
  - **ip addr add \<IP_adress> dev \<interface>** - assigns an IP address to an interface
  - **ip addr del \<IP_adress> dev \<interface>** - deletes an assigned IP address to an interface
  - **ip link set \<interface> up** - enables a network interface
  - **ip link set \<interface> down** - disables a network interface
  - **ip monitor** - monitors and displays the state of devices, addresses, and routes continuously
* **iptables / ufw** - firewall configuration
  - **iptables -t \<table>** - option that sets chosen table \(set of chains\), tables: filter, nat, mangle, raw, security
  - **iptables -t \<table> -A/-C/-D \<chain>** - options that append (-A), check if exists (-C), delete (-D) rules to the given chain \(set of rules\), chains: INPUT, FORWARD, OUTPUT, PREROUTING, POSTROUTING
  - **iptables -t \<table> -A/-C/-D \<chain> -p \<protocol_name>** - option that matches protocol that packet follows, possible values: tcp, udp, icmp, ssh, etc.
  - **iptables -t \<table> -A/-C/-D \<chain> -s \<source_address>** - option that matches given source address of the packet
  - **iptables -t \<table> -A/-C/-D \<chain> -d \<destination_address>** - option that matches given destination address of the packet
  - **iptables -t \<table> -A/-C/-D \<chain> -i \<interface>** - option that matches packets with the specified in-interface
  - **iptables -t \<table> -A/-C/-D \<chain> -o \<out_interface>** - option that matches packets with the specified out-interface
  - **iptables -t \<table> -A/-C/-D \<chain> -j \<action>** - option that specifies action to be taken on a match, possible actions: ACCEPT, DROP, QUEUE, RETURN
  - **iptables --flush** - option that removes all filtering rules
* **nslookup \<domain/IP_address>** - displays information from DNS server, querying domain names and IP addresses
* **scp** - securely copies files between systems
  - **scp \<file> \<remote_username@remote_host\:remote_directory>** - securely copies files from local to remote system
  - **scp -r \<directory_path> \<remote_username@remote_host\:remote_directory>** - securely, recursively copies directory from local to remote system
  - **scp \<remote_username@remote_host\:/home/user/remote_path> \<local_path>** - securely copies files from remote to local system
## SSH
* **ssh-keygen** - generates pair of SSH keys
  - **ssh-keygen -t rsa -b 4096 -C \<your_email>** - typical key generation
* **ssh-copy-id** - copies public SSH key to remote server
  - **ssh-copy-id \<remote_user@remote_host>** - typical key coping
* **ssh -i \<path_to_private_key> \<remote_user@remote_host>** - securely connects to remote systems, -i stands for specifing private SSH key to use
## Package management
* **apt** - managing packages in Ubuntu/Debian
  - **apt update** - updates packages
  - **apt update && apt upgrade** - upgrades system
  - **apt install \<package_name>** - installs package of given name
  - **apt remove \<package_name>** - removes package of given name
* **yum** - managing packages in CentOS/RHEL
  - **yum update -y** - updates packages
  - **yum install \<package_name>** - installs package of given name
  - **yum remove \<package_name>** - removes package of given name
## Other
* **tar \<options> \<archive_file> \<file_or_directory_to_be_archived>** - creates and extracts tar archives
  - **-c** - creates an archive by bundling files and directories together
  - **-x** - extracts files and directories from an existing archive
  - **-f** - specifies the filename of the archive to be created or extracted
  - **-t** - displays or lists the files and directories contained within an archive
  - **-u** - archives and adds new files or directories to an existing archive
  - **-v** - displays verbose information, providing detailed output during the archiving or extraction process
  - **-A** - concatenates multiple archive files into a single archive
  - **-z** - uses gzip compression when creating a tar file, resulting in a compressed archive with the '.tar.gz' extension
  - **-j** - uses bzip2 compression when creating a tar file, resulting in a compressed archive with the '.tar.bz2' extension
  - **-W** - verifies the integrity of an archive file, ensuring its contents are not corrupted
  - **-r** - updates or adds files or directories to an already existing archive without recreating the entire archive
  - **tar cvzf \<archive_file> \<file_or_directory_to_be_archived>** - typical compression
  - **tar xvzf \<archive_file>** - typical extraction
* **crontab** - time-based job scheduler that schedules commands or scripts to run at specified times
  - **crontab -l** - list current crontab entries
  - **crontab -e** - edit crontab entries
  - **How it works?**\
  MIN HOUR DOM MON DOW CMD\
  MIN \(Minute\) - specifies the minute when the command will run\
  HOUR \(Hour\) - denotes the hour of the day when the command is scheduled to execute\
  DOM \(Day of Month\) - specifies the day of the month for the task\
  MON \(Month\) - indicates the month during which the command will be executed\
  DOW \(Day of Week\) - specifies the day of the week for the task\
  CMD \(Command\) - represents the actual command or script that will run at the scheduled time\
  \* value represents all the possible units - e.g. every minute of every hour throughout the year\
  The comma-separated value in a field specifies that the command needs to be executed at all the mentioned times\
  The dash-separated value in a field specifies that the command needs to be executed within a specific range of time\
  Keywords @yearly, @montly, @daily, @hourly, @reboot can be used to specific typical times.
