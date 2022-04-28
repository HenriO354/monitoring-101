[README.md](README.md#sub-section)
[research-notes.md](research-notes.md#sub-section)

- # 1) Detecting system bottlenecks

- # 2) Disk (storage)

- # 3)  CPU and memory Bottlenecks

- # 4)  Network bottleneck


![This is an image](/assets/images/ps.png)

# 1) Detecting system bottlenecks

Linux finds out what processes are using Swap space<br>

    #smem    
![This is an image](/assets/images/smem.png)

# Top Memory Usage

Linux finds out what processes are using Swap space<br>

![This is an image](/assets/images/top-HP-henri.png)
<br>From the command above, the option:

    -b : runs top in batch mode
    -o : used to specify fields for sorting processes
    head utility displays the first few lines of a file and
    the -n option is used to specify the number of lines to be displayed.

Note that head utility, by default displays the first ten lines of a file, that is when you do not specify the number of lines to be displayed. Therefore, in the example above, we displayed the first 22 lines of top command output in batch mode.

# Memory Utilization Slabinfo ##

# vmstat -m : <br>Get Information About Active / Inactive Memory Pages</b>

![This is an image](/assets/images/vmstat-m.png)

# vmstat -a – Virtual Memory Statistics

![This is an image](/assets/images/vmstat-a.png)

vmstat is a Linux command tool which collects and analyze data about your system’s memory, swap, kernel threads, disks, system processes, I/O blocks, CPU activity and much more in real time. With the help of this Linux performance tool, you can find out the cause of the problem and issue related to system memory.<br>

# iotop – Monitor Linux Disk I/O

![This is an image](/assets/images/iotop.png)

Like <b>“Top”</b> command and <b>“Htop”</b> program, <b>"iotop"</b> is a python program to show you I/O usages data through “Top” like interface. This tool lets you monitor <u>real-time disk I/O and process. Moreover, you can also check the high used disk read and write time for the threads or process</u>.


# 2) Disk (storage)
    df

![This is an image](/assets/images/df.png)

# 3) CPU and memory bottlenecks
    glances
![This is an image](/assets/images/glances.png)



# 4) Network bottleneck
# iptraf-ng

![This is an image](/assets/images/iptraf-ng.png)
