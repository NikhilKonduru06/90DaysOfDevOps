## check running processes 
   1. ps aux
      Output :
      USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
      root           1  0.6  1.4  22108 13528 ?        Ss   07:31   0:01 /sbin/init
      root           2  0.0  0.0      0     0 ?        S    07:31   0:00 [kthreadd]
      root           3  0.0  0.0      0     0 ?        S    07:31   0:00 [pool_workqueue_release]
      root           4  0.0  0.0      0     0 ?        I<   07:31   0:00 [kworker/R-rcu_gp]
      root           5  0.0  0.0      0     0 ?        I<   07:31   0:00 [kworker/R-sync_wq]
   
   2.  top - display Linux processes
       Output :
       top - 07:38:15 up 6 min,  1 user,  load average: 0.02, 0.02, 0.00
    Tasks: 109 total,   1 running, 108 sleeping,   0 stopped,   0 zombie
    %Cpu(s):  0.0 us,  0.0 sy,  0.0 ni, 99.8 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
    MiB Mem :    914.2 total,    369.5 free,    357.4 used,    344.4 buff/cache
    MiB Swap:      0.0 total,      0.0 free,      0.0 used.    556.8 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1053 ubuntu    20   0   12352   5868   3656 R   0.3   0.6   0:00.01 top
      1 root      20   0   22108  13528   9652 S   0.0   1.4   0:01.08 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd

   3. pgrep -  look up, signal, or wait for processes based on name and other attributes
      Output :
      pgrep -c ping
      0

## Service Checks
  1.  systemctl - Control the systemd system and service manager
      Output:
      State: running
      Units: 434 loaded (incl. loaded aliases)
      Jobs: 0 queued
      Failed: 0 units
      Since: Thu 2026-02-19 07:31:45 UTC; 12min ago
      systemd: 255.4-1ubuntu8.11
  
    2.systemctl list-units
    Output:
    UNIT                                                                         LOAD   ACTIVE SUB       DESCRIPTION                  >
    proc-sys-fs-binfmt_misc.automount                                            loaded active running   Arbitrary Executable File For>
    sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p1.device      loaded active plugged   Amazon Elastic Block Store cl>
    sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p14.device     loaded active plugged   Amazon Elastic Block Store 14
    sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p15.device     loaded active plugged   Amazon Elastic Block Store UE>
    sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p16.device     loaded active plugged   Amazon Elastic Block Store BO>
    sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1.device                loaded active plugged   Amazon Elastic Block Store

## Log Checks
   1. journalctl -u ssh
      Output:
      Jan 31 05:44:42 ip-172-31-40-13 systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
      Jan 31 05:44:42 ip-172-31-40-13 sshd[1148]: Server listening on 0.0.0.0 port 22.
      Jan 31 05:44:42 ip-172-31-40-13 sshd[1148]: Server listening on :: port 22.
      Jan 31 05:44:42 ip-172-31-40-13 systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
   
   2. journalctl -u ssh | tail -n 50
      Output:
      Feb 08 06:37:49 ip-172-31-40-13 sshd[2296]: pam_unix(sshd:session): session opened for user ubuntu(uid=1000) by ubuntu(uid=0)
      Feb 08 06:38:50 ip-172-31-40-13 sshd[2385]: banner exchange: Connection from 142.93.97.172 port 42346: invalid format
      Feb 08 06:38:50 ip-172-31-40-13 sshd[2386]: banner exchange: Connection from 142.93.97.172 port 42352: invalid format
      Feb 08 07:43:33 ip-172-31-40-13 sshd[1515]: Received signal 15; terminating.
