A consistent hashing scheduler for LVS
======================================

A consistent hashing scheduling module for <a href="http://www.linuxvirtualserver.org/">LVS(Linux Virtual Server)</a>

<a href="http://en.wikipedia.org/wiki/Consistent_hashing">Consistent hashing</a> is a better algorithm than mod, for the latter might cause most of connections lose when the back-end servers is changed. 
In our case, we need support stickiness for multiple directors in LVS, so the consistent-hashing solution is a nice choice.

How to compile:
----------------
	a, install dependencies: gcc kernel-headers kernel-devel(yum or apt-get)
            # for Ubuntu with source repo configured in apt
            - sudo apt-get build-dep linux-image-$(uname -r)

            # OR.. shortcut
            sudo apt-get install build-essential linux-headers-$(uname -r)
	b, make modules
	c, make modules_install

How to check if ip_vs_ch is installed:
--------------------------------------
	a, modprobe ip_vs_ch
	b, lsmod | grep ip_vs_ch

Issues:
-------
a, if the current kernel version(uname -r) is different from the kernel-devel package might cause module compile or install issue:

    upgrade your kernel or find the kernel-devel package to match the current kernel

References:
-----------
a, Consistent hashing library comes from <a href="http://www.codeproject.com/Articles/56138/Consistent-hashing">libconhash</a>

License:
--------
The ip_vs_ch is under GNU GPLv2 License
