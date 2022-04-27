[README.md](README.md#sub-section)
[system-report](system-report.md#sub-section)

# What are the **most memory intensive** running processing ?

##  Process:    ##
A process may refer to :
- A **set of instructions** 
being processed by the computer processor.

For example, in Windows you can see each of the processes running by opening the Processes tab in Task Manager. Windows Processes are Windows Services and background programs you normally don't see running on the computer. A process may be a printer program that runs in the background and monitors the ink levels and other printer settings while the computer is running.

A typical computer has multiple processes running all the time to help manage the operating system, its hardware, and the software running on the computer.

Here is an example on how the list of top processes ordered by RAM and CPU use in descendant form (remove the pipeline and head if you want to see the full list):

The following command will show the list of top processes ordered by RAM and CPU use in descendant form (remove the pipeline and head if you want to see the full list):

![This is an image](/assets/images/Screenshot%202022-04-27%20at%2008-59-14%20Find%20Top%20Running%20Processes%20by%20Highest%20Memory%20and%20CPU%20Usage%20in%20Linux.png)

Sample Output

![This is an image](/assets/images/Screenshot-%20FindTopRunningProcessesbyHighestMemory_andCPUUsageinLinux.png)



## Find Top Running Processes by Highest Memory and CPU Usage in Linux##

I remember once reading that efficient system administrators are lazy people. The reason is not that they’re not doing their job or wasting their time – it is mostly because they have automated a good deal of their routine tasks. Thus, they don’t have to babysit their servers and can use their time to learn new technologies and always stay at the top of their game.

Part of automating your tasks, is learning how to get a script do what you would have to do yourself otherwise. Continually adding commands to your own knowledge base is just as important.

For that reason, in this article we will share a trick to find out, which processes are consuming lots of Memory and CPU utilization in Linux.

![This is an image](/assets/images/Find-Top-Processes-By-RAM-and-CPU-Usage.png)

Brief explanation of above options used in above command:

The -o (or –format) option of ps allows you to specify the output format. A favorite of mine is to show the processes’ PIDs (pid), PPIDs (pid), the name of the executable file associated with the process (cmd), and the RAM and CPU utilization (%mem and %cpu, respectively).

Additionally, I use --sort to sort by either %mem or %cpu. By default, the output will be sorted in ascendant form, but personally I prefer to reverse that order by adding a minus sign in front of the sort criteria.

To add other fields to the output, or change the sort criteria, refer to the OUTPUT FORMAT CONTROL section in the man page of ps command.

Don’t Miss: Find [Top 15](https://www.tecmint.com/find-processes-by-memory-usage-top-batch-mode/) Processes by Memory Usage with ‘top’ in Batch Mode

# <b>Summary: #

Monitoring process is one of the numerous tasks of a Linux server system administrator, in this tip, we looked at how you list processes on your system and sort them according to RAM and CPU use in descendant form using the ps utility.

# What are log files ?
Linux Logging Basics

Operating system logs provide a wealth of diagnostic information about your computer, and Linux is no exception. 

Everything from kernel events to user actions are logged by Linux, allowing you to see almost any action performed on your servers. In this section, we’ll explain what Linux logs are, where you can find them, and how to interpret them.

Linux System Logs

Linux has a special directory for storing logs called /var/log. This directory contains logs from the OS itself, services, and various applications running on the system. Here’s what this directory looks like on a typical Ubuntu system.

*Where* can you find them on a *typical Linux* system ?
![This is an image](/assets/images/System-log-terminal.png)

Some of the most important Linux system logs include:

/var/log/syslog and /var/log/messages store all global system activity data, including startup messages. Debian-based systems like Ubuntu store this in /var/log/syslog, while Red Hat-based systems like RHEL or CentOS use /var/log/messages.

/var/log/auth.log and /var/log/secure store all security-related events such as logins, root user actions, and output from pluggable authentication modules (PAM). Ubuntu and Debian use /var/log/auth.log, while Red Hat and CentOS use /var/log/secure.

/var/log/kern.log stores kernel events, errors, and warning logs, which are particularly helpful for troubleshooting custom kernels.

/var/log/cron stores information about scheduled tasks (cron jobs). Use this data to verify that your cron jobs are running successfully.

Some applications also write log files in this directory. For example, the Apache web server writes logs to the /var/log/apache2 directory (on Debian), while MySQL writes logs to the /var/log/mysql directory. Some applications also log via syslog.

Syslog Format and Fields

Syslog messages contain a standardized header with several fields. These include the timestamp, the name of the application that generated the event, the location in the system where the message originated, and its priority. You can change this format in your syslog implementation’s configuration file, but using the standard format makes it easier to parse, analyze, and route syslog events.

Here is an example log message using the default format. It’s from the sshd daemon, which controls remote logins to the system. This message describes a failed login attempt:

Jun 4 22:14:15 server1 sshd[41458] : Failed password for root from 10.0.2.2 port 22 ssh2

You can also add additional fields to your syslog messages. Let’s repeat the last event after adding a few new fields. We’ll use the following rsyslog template, which adds the priority (<%pri%>), protocol version (%protocol-version%), and the date formatted using RFC 3339 (%timestamp:::date-rfc3339%):

<%pri%>%protocol-version% %timestamp:::date-rfc3339% %HOSTNAME% %app-name% %procid% %msgid% %msg%n

This generates the following log:

<34>1 2019-06-05T22:14:15.003Z server1 sshd - - pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.2.2

Below, you’ll find descriptions of some of the most commonly used syslog fields when searching or troubleshooting issues.

Timestamp

The timestamp field indicates the time and date the message was generated on the system sending the message. The example timestamp breaks down like this:

    “2019-06-05”is the year, month, and day.
    “T”is a required element of the timestamp field, separating the date and the time.
    “22:14:15.003”is the 24-hour format of the time, including the number of milliseconds (003).
    “Z”indicates UTC time. Instead of z, the example could have included an offset, such as -08:00, which indicates that the time is offset from UTC by eight hours.

Hostname

The hostname field (“server1” in the example above) indicates the name of the host or system that originally sent the message.

App-Name

The app-name field (“sshd:auth” in the example) indicates the name of the application that sent the message.

Priority

The priority field or pri for short (“<34>” in the example above) tells you how urgent or severe the event is. It’s a combination of two numerical fields: the facility and the severity. The facility specifies the type of process that created the event, ranging from 0 for kernel messages to 23 for local applications. The severity ranges from 0–7, with 0 indicating an emergency and 7 indicating a debug event.

Pri can be output in two ways. The first is as a single number, prival, which is calculated as the facility field value multiplied by eight, then the result is added to the severity field value: (facility)(8) + (severity). The second is pri-text, which will output in the string format “facility.severity”. The latter format can often be easier to read and search, but takes up more storage space.
Logging with Systemd

Many Linux distributions ship with systemd, which is a process and service manager. Systemd implements its own logging service called journald that can replace or complement syslog. Journald logs in a significantly different manner than systemd, which is why it has its own section in the Ultimate Guide to Logging. You can learn more about logging via systemd in the Systemd Logging section.
Additional Resources

Check this out :)
[How to View and Configure Linux Logs on Ubuntu and CentOS ](https://www.digitalocean.com/community/tutorials/how-to-view-and-configure-linux-logs-on-ubuntu-and-centos) 


# List of Linux Monitoring Tools For SysAdmin

    1.   Command Line Tools
    _______________________

- **“Top”** command is a Linux performance monitoring tool which comes pre-installed in many Linux or Unix system. “Top” command comes handy when you need to have an overview of all the threads or process running in the system.

![This is an image](/assets/images/Top.jpg)
    It displays various system information including Memory usage, CPU usage, Swap Memory, Buffer Size, Cache Size, Process PID, etc. It also shows the excessive use of memory and CPU of a system running process ;
  
- **Mytop** is a MySQL thread and performance monitoring tool which let you have a close look into the database and queries that’s processing in the real times ;

- **Htop** is an advanced Linux process monitoring tool which is similar to “Top” but offers some rich features like interactive process viewer, vertical and horizontal process viewer, shortcut keys, etc. It’s a third-party Linux monitoring tool that doesn’t come pre-installed in Linux or Unix system. You need to download and install it in the system.

- **Atop** is a Linux performance monitoring tool which provides reporting of all system threads or process, daily system logging, process activity for long-term data analysis, overloaded system resources, etc. It also shows the system activity on CPU, memory, swap, disks (including LVM) and network layers.

# Linux Network Monitoring Tools

Ensuring a healthy and smooth running system is one of the priority tasks to any Linux administrator. Here I will discuss a generic list of best Linux network monitoring tools:

    2.  Tools

- **jnettop** – Linux Bandwidth Monitor
ntopng – A Network Traffic Monitor

If you have liked ntop, then you are going to love ntopng also. It’s a next-generation version of ntop. This tool will provide you with a web-based graphical user interface to monitor network usages and traffic. It’s a cross-platform tool which runs on every Unix platform, MacOSX and Windows as well.
EtherApe

- **EtherApe** is a free and open source graphical network monitor for Unix system. It can show you live network traffic or capable of reading it from tcpdump. It supports Ethernet, token ring, PPP, FDDI, WLAN devices, and several encapsulation formats.
BandwidthD

- **BandwidthD** is one of the best network monitoring tools for Linux, Unix system, and Windows. BandwidthD tracks usages of TCP or IP network subnets and provides a visualized graph image based on an HTML web page. It has a DB driven system that supports filtering, searching, custom reports, multiple sensors, etc.
ethtool – Linux Network Drivers and Hardware Controller

- **ethtool** is a fantastic Linux utility tool that controls wired Ethernet devices. It can be used to get identification and diagnostic information, extended device information, etc. ethtool can control speed, duplex, auto-negotiation, and flow of Ethernet devices.
ngrep

- **ngrep** is a  PCAP-based tool and like GNU grep but applicable for the network layer that let you dictate hexadecimal or an extended expression to match against data payloads of network packets. It supports various network protocols including ICMPv4/6, IPv4/6, UDP, TCP, IGMP, RAW, etc. Moreover, It also understands BPF filter logic just like various packet sniffing tools such as Snoop and tcpdump.
IPTraf – Real-Time IP LAN Monitoring

- **IPTraf** is one of the best free and open source CLI based Linux Monitor Network Traffic Tools available in the market. It collects and displays various useful information including IP traffic passing over the network, packet and bytes count, TCP flag information, OSPF packet types, ICMP details, TCP/UDP traffic breakdowns, etc. It supports various interface like local loopback, Ethernet and FDDI interfaces, SLIP, PPP, Parallel Line IP and much more.

- **NetHogs** – Linux Bandwidth Monitor
    NetHogs is an open source network monitoring software similar to Linux Top command but a small “net top” tool which helps you to monitor Linux Network traffic and bandwidth not breaking the traffic down per subnet or protocol rather grouping it by the network bandwidth process. This network monitoring software is helpful to find out which PID is suddenly taking a lot of network traffic and bandwidth and gone wild a bit.
- **MRTG** – Router Traffic Monitor

    If you are using a network router and wants to know what it does, then MRTG monitoring tool is for you. Though initially, the main aim was to monitor only router traffic, now it can do multiple network monitoring tasks as well.

    It can monitor SNMP network devices and let you know how much traffic has passed using each thread. It provides the stats in an easily understandable picture and HTML pages. MRTG is a free, open source software written in Perl programming language and works on Windows, Linux/BSD system, and even Netware systems.

- **Traceroute**

    **Traceroute** is a built-in system tool for understanding the network route and estimating the delay of packets throughout the network interface.

- **bmon** – Linux Bandwidth Monitor

    **bmon** is a network monitoring and debugging tool to get various stats related to networking and prepare them in an easily understandable way. It supports various output methods like a programmable text output for scripting and an interactive curses user interface.

- **netstat** – Network Statistics

    **Netstat** – Network Statistics is one of the best command line tools for monitoring network incoming and outgoing packets and interface statistics. This network monitoring software is very useful and handy for a system administrator to identify or troubleshoot network related issues and monitor Linux network performance as well.
- **IPTState**

    **IPTState – IP Tables State** is a top-like tool that let you get an interactive session to watch where traffic is crossing your iptables firewall/Netfilter connection. You can sort this data and limit the view by various criteria.

- **darkstat** – Linux Monitor Network Traffic

    **darkstat** is a small, single threaded, portable, and efficient open source network monitoring software that capture network traffic, calculates usages stats, and display reports over HTTP. It supports IPv6 and asynchronous reverse DNS resolution using a child process.
tcpdump – Network Packet Analyzer

- **Tcpdump** is a network packet analyzer or packets sniffer software which runs on almost all the dominant Linux distributions. It’s one of the widely used and recommended command line Linux monitoring tools which is used to filter or capture TCP/IP packets that transferred or received on a specific network connection. You can also export or save captured packages in a file for further advanced analysis.
- **ss**

    “**ss**” is a Linux command tool which is alternative to the “netstat” network monitoring program. This command is faster and gives more system stats than netstat.
- **Justniffer** – Network TCP Packet Sniffer

    **Justniffer** is a network protocol analyzer and TCP packet sniffer tool that captures both low level and high-level network traffic data and produces a customized log from Apache web server log f
- **MTR**

    **mtr** is a network diagnostic tool which combines the functionality of both ‘traceroute’ and ‘ping’ programs. When mtr gets its first run on a system, It checks the network connection the host that mtr runs on and a user-specified host service.

- **Mpstat**

- **Mpstat** is one of the Linux network monitoring tools that collects and shows the information on **CPU** utilization and performance statistics. Without using any option, it will display the Global Average Activities. With option ‘-p’ and ‘ALL’ displays statistics one by one that starts from 0. To get all the information in a single command, put ‘-u-I ALL -p ALL’. in a word, this command system reports overall processor related data.


# How can you check who were the last connected users ?

If you are working in a medium to big-sized company, it is quite likely that you are working with many other system administrators.

As you are performing your sysadmin tasks, some users may try to connect to your server in order to perform their daily tasks.

However, in some cases, you may find that something has changed on your server. As a consequence, you are wondering who performed the change.

Luckily for you, there are many ways to find who last logged in on your server.

In this tutorial, you will learn about the different useful commands that you can use in order to check the last logins on your computer.
[Here is how to](https://devconnected.com/how-to-find-last-login-on-linux/)


# What are the different metrics of health and performance of a system?

Try these built-in commands and a few add-on tools. Most distributions come with tons of Linux monitoring tools. These tools provide metrics which can be used to get information about system activities. You can use these tools to find the possible causes of a performance problem. The commands discussed below are some of the most fundamental commands when it comes to system analysis and debugging Linux server issues such as:

- Finding out system bottlenecks
- Disk (storage)
- bottlenecks
- CPU and memory bottlenecks
- Network bottleneck.

1. top – Process activity monitoring command

top command display Linux processes. It provides a dynamic real-time view of a running system i.e. actual process activity. By default, it displays the most CPU-intensive tasks running on the server and updates the list every five seconds.
top - Linux monitoring command

[top](https://www.cyberciti.biz/tips/wp-content/uploads/2009/06/top-Linux-monitoring-command.jpg)

Fig.01: Linux top command
Commonly Used Hot Keys With top Linux monitoring tools

Here is a list of useful hot keys:
Hot Key 	Usage
t 	Displays summary information off and on.
m 	Displays memory information off and on.
A 	Sorts the display by top consumers of various system resources. Useful for quick identification of performance-hungry tasks on a system.
f 	Enters an interactive configuration screen for top. Helpful for setting up top for a specific task.
o 	Enables you to interactively select the ordering within top.
r 	Issues renice command.
k 	Issues kill command.
z 	Turn on or off color/mono

How do I Find Out Linux CPU Utilization?
2. vmstat – Virtual memory statistics

The vmstat command reports information about processes, memory, paging, block IO, traps, and cpu activity.
# vmstat 3

Sample Outputs:

    procs -----------memory---------- ---swap-- -----io---- --system-- -----cpu------
    r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
    0  0      0 2540988 522188 5130400    0    0     2    32    4    2  4  1 96  0  0
    1  0      0 2540988 522188 5130400    0    0     0   720 1199  665  1  0 99  0  0
    0  0      0 2540956 522188 5130400    0    0     0     0 1151 1569  4  1 95  0  0
    0  0      0 2540956 522188 5130500    0    0     0     6 1117  439  1  0 99  0  0
    0  0      0 2540940 522188 5130512    0    0     0   536 1189  932  1  0 98  0  0
    0  0      0 2538444 522188 5130588    0    0     0     0 1187 1417  4  1 96  0  0
    0  0      0 2490060 522188 5130640    0    0     0    18 1253 1123  5  1 94  0  0

Display Memory Utilization Slabinfo

# vmstat -m
Get Information About Active / Inactive Memory Pages

# vmstat -a

See “How do I find out Linux Resource utilization to detect system bottlenecks?” for more info.
Linux Find Out What Process Are Using Swap Space

Use the smem command:
smem

Another option is to combine pgrep command with the grep command to find out SWAP usage:

pgrep memcached
grep --color VmSwap /proc/48440/status

Linux Find Out What Process Are Using Swap Space

Linux Find Out What Process Are Using Swap Space
3. w – Find out who is logged on and what they are doing
w command displays information about the users currently on the machine, and their processes.
# w username
# w vivek

Sample Outputs:

    17:58:47 up 5 days, 20:28,  2 users,  load average: 0.36, 0.26, 0.24
    USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
    root     pts/0    10.1.3.145       14:55    5.00s  0.04s  0.02s vim /etc/resolv.conf
    root     pts/1    10.1.3.145       17:43    0.00s  0.03s  0.00s w

4. uptime – Tell how long the Linux system has been running
uptime command can be used to see how long the server has been running. The current time, how long the system has been running, how many users are currently logged on, and the system load averages for the past 1, 5, and 15 minutes.
# uptime

Output:

        18:02:41 up 41 days, 23:42,  1 user,  load average: 0.00, 0.00, 0.00

1 can be considered as optimal load value. The load can change from system to system. For a single CPU system 1 – 3 and SMP systems 6-10 load value might be acceptable.


# How can you check the uptime of a machine?

uptime – Tell how long the Linux system has been running
uptime command can be used to see how long the server has been running. The current time, how long the system has been running, how many users are currently logged on, and the system load averages for the past 1, 5, and 15 minutes.

    uptime

Output:

    18:02:41 up 41 days, 23:42,  1 user,  load average: 0.00, 0.00, 0.00

<br>1 can be considered as optimal load value. The load can change from system to system. For a single CPU system 1 – 3 and SMP systems 6-10 load value might be acceptable.

# How can you assess the network traffic?

iptraf – Get real-time network statistics on Linux
iptraf command is interactive colorful IP LAN monitor. It is an ncurses-based IP LAN monitor that generates various network statistics including TCP info, UDP counts, ICMP and OSPF information, Ethernet load info, node stats, IP checksum errors, and others. It can provide the following info in easy to read format:

    - Network traffic statistics by TCP connection
    - IP traffic statistics by network interface
    - Network traffic statistics by protocol
    - Network traffic statistics by TCP/UDP port and by packet size
    - Network traffic statistics by Layer2 address

Iptraf-ng network monitoring tool
Network monitoring with iptraf-ng

iptraf-ng is a menu driven utility that allows you to monitor your TCP network. Information such as ICMP, OSPF, TCP and UDP counts can be displayed easily. 

Example install in CentOS 8

Command issued to install: dnf install iptraf-ng

![iptraf-ng](/assets/images/iptraf-ng_01.png)

Interfaces can be monitored. Monitor connectivity and traffic with ease. This package was formerly known as "iptraf", however, it has been updated and is now called "iptraf-ng" - iptraf - next generation.
Installing iptraf-ng

iptraf-ng can be installed directly from the repositories on the following systems:

To install iptraf-ng on a Debian/Ubuntu/Mint system, issue the command: sudo apt install iptraf-ng

To install iptraf-ng on a openSUSE system, issue the command: zypper install iptraf-ng

To install htop on a RHEL 8 or CentOS 8 system, issue the command: dnf install iptraf-ng
Example install in CentOS 8

Command issued to install: dnf install iptraf-ng

# iptraf-ng main menu

To start iptraf-ng, you must issue the following command: sudo iptraf-ng"

![iptraf-ng](monitoring-101/assets/images/iptraf-ng_01.png)