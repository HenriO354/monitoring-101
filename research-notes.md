# What are the most memory intensive

- item
  - item

- item

-

# What are log files ?

- Where can you find them on a *typical Linux* system ?

# How can you check who were the last connected users

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

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

## [sub-section](system-report.md#sub-section)

