# localuser-script
Bash script that will create a local user account on linux

The script needs to be executed as a root or root permission.

An example execution of the script:

$ localuser
ERROR: you must be administrator to execute 'localuser'
$ sudo localuser
try 'localuser help'
$ sudo localuser help
usage: localuser command [options]
where command is:
    help [command]
    add name [options]
    for more specific help, try 'localuser help add'
$ sudo localuser help add
usage: localuser add login [options]
where options are:
    --home dir        - set the home directory to 'dir'
    --name fullname   - set the username to 'fullname'
    --shell sh        - set user shell to 'sh'
    --skel dir        - use skeleton directory 'dir' to build user home
    --noexec          - do not execute the commands, print them
$

The scripts uses a 'command' to add users. Below is some more interactions:
 
$ sudo localuser add andrew
user andrew added
$ sudo localuser add andrew
ERROR: andrew already exists as a user
$ sudo localuser add mj --dir /home/mark.jacob --name "Mark Jacob" --shell /bin/csh
user mj added
$ sudo localuser add alice --noexec
echo "alice:x:1005:1006::/home/alice:/bin/bash" >> /etc/passwd
echo "alice:!:17465:0:99999:7:::" >> /etc/shadow
echo "alice:x:1006:" >> /etc/group
echo "alice:!::" >> /etc/gshadow
cp /etc/skel /home/alice
chown -R alice:alice /home/alice
$



