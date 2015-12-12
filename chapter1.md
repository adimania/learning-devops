# What is Linux?
Linux is any operating system which uses Linux Kernel for managing system resources. Linux Kernel, itself, is licensed under GNU General Public License. This ensures that anyone can read, understand and modify the kernel to suit their needs. However, modificatoin is not a part of this course, and it is not required for most of the common usecases. 

## Tools of the trade
First of all, we will check out the tools of the trade. A brief summary is given below. We'll discuss these tools in detail as we go ahead.

* top: This tells you what processes are running and which ones are consuming more resources. This is real-time.
* free: This will show how much free memory you have.
* iotop: This tool offers dynamic view of how much disk operations are happening and who is doing them. This tools give a real-time view.
* netstat: This tool helps us in discovering network information like port usage, routing tables etc.
* ps: This tools gives a list of processes running in our systems. Since, unlike top, this does not offer a dynamic view, it is easier to write scripts using ps.
* kill: This command is used to pass on IPC signals to processes.
* sar: This tool is used to record the system stats like cpu, load, ram etc.

### Concepts
* Load average: Load average quantifies the number of processes in runnable state. A one minute load average of 2.5 on a quad core machines essentially means that within last one minute, there were 2.5 processes demanding for CPU resoueces. Since we have four cores, our system was underutilized. 
* ulimit: Linux system puts limits on resources. These limits are defined in limits.conf. There are two kinds of limits, hard limit and soft limit. An unprivileged process can change only its soft limit up to a maximum of hard limit. 