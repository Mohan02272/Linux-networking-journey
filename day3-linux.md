FILE PERMISSIONS & OWNERSHIP:

Every file has 3 types of access:

Read (r) → view content
Write (w) → modify content
Execute (x) → run file/program

rwx = 7
rw- = 6
r-- = 4

And 3 types of users:

Owner (u) → file creator
Group (g) → users in same group
Others (o) → everyone else

To check Permission : ls -l
To change Permission of a specific file : chmod u+x/g-w/o-r <filename>
To change ownsersip of a file : chown user <filename>
To change owner and group of a file : chown user:group <filename>


FIREWALL BASICS

Firewall = traffic filter

It decides:

Allow traffic
Block traffic

To check traffic rules: sudo iptables -L

To Allow SSH : sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

Break:

-A INPUT =  add rule to input
-p tcp = protocol
--dport 22 = SSH port
ACCEPT = allow

To block HTTP: sudo iptables -A INPUT -p tcp --dport 80 -j DROP

Break:

-A INPUT = add rule to input
-p tcp = protocol
--dport 80 = HTTP port
DROP = Block

To delete any rule : sudo iptables -D INPUT 1

To check Firewall status : sudo systemctl status firewalld
To start Firewall : sudo systemctl start firewalld
To enable Firewall : sudo systemctl enable firewalld

To allow any service through firewall: 
sudo firewall-cmd --permanent --add-service=<service-name>
sudo firewall-cmd --reload

To Allow Port through Firewall:
sudo firewall-cmd --permanent --add-port=<port-num>/tcp
sudo firewall-cmd --reload

To remove any rule :
sudo firewall-cmd --permanent --remove-port=<port-num>/tcp
sudo firewall-cmd --reload



SSH CONFIGURATION

SSH = Secure Shell
Used to remotely access Linux servers.

To Install SSH server : sudo apt install openssh-server -y
To Check status : sudo systemctl status ssh
To start SSH service : sudo systemctl start ssh
To enable SSH Service : sudo systemctl enable ssh
To connect any server from another machine: ssh user@ip_address
To check ssh config file : sudo cat /etc/ssh/sshd_config

To Hardening SSH :
1. Change port
2. Disable root login
3. Allow only specific users
4. After changes restart SSH.

