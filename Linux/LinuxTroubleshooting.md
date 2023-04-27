101 Linux Troubleshooting Killing a port pro@pro-H55M-USB3:~$ sudo netstat -natlp | grep 8888
[sudo] password for pro:
tcp6 0 0 127.0.0.1:8888          :::*                    LISTEN 16310/java      
pro@pro-H55M-USB3:~$ kill 16310 pro@pro-H55M-USB3:~$ sudo netstat -natlp | grep 8888

sudo netstat -lpn |grep :8080

kill 6782 or killall -9 java

lsof -i :4848

First you can hit Alt+ F2, type xkill, and hit enter. Your mouse cursor will then turn into an X. Hover over the
offending window and left-click to kill it. Right clicking will cancel and return your mouse to normal. If your program
is running from a terminal, on the other hand, you can usually halt it with Ctrl + C. If not Or When the mouse stops
working:
If the keyboard still works, hit Alt + F2 and run gnome-terminal if these fail to launch, hit Alt-Ctrl + F1 and login
with your username and password). From there you can troubleshoot things. I'm not going to get into mouse
troubleshooting here, as I haven't researched it. If you just want to try restarting the GUI, run sudo service lightdm
restart. This should bring down the GUI, which will then attempt to respawn, bringing you back to the login screen.
Second killall -9 cinnamon export DISPLAY=:0.0; cinnamon Cinnamon freezes Switch tty. I usually go to tty6, Ctrl+Alt+F6
If you need to login first, do so. Type w (yes, just the letter) and press enter. This commands does a lot of different
things, but you need it to figure out the number of the display you are using. The display number is in the column FROM.
Mine is :0 (yes, including the colon). Assuming that cinnamon is already dead (which you would notice by the windows
lacking titles and that you can't move different windows around, and perhaps even not being able to use the keyboard),
you type export DISPLAY=:0; cinnamon &, and don't forget the colon. I add the ampersand (&) only not to keep that tty
busy. Third Get and kill the process username$ ps ax | grep firefox 2222 ? S 0:00 /bin/sh /usr/lib/firefox-3.6.9/firefox
2231 ? Sl 514:36 /usr/lib/firefox-3.6.9/firefox-bin 30290 pts/2 S+ 0:00 grep --color=auto firefox End it with
kill [process ID here]. If that fails despite waiting a few seconds, try sending a SIGHUP: kill -HUP [process ID here].
If all else fails, as a last resort send SIGKILL (-9): kill -9 [process ID here]. Note that you should only use SIGKILL
as a last resort, because the process will be terminated immediately with no opportunity for cleanup. If it locks up
completely, you can REISUB it, which is a safer alternative to just cold rebooting the computer. REISUB by:
While holding Alt and the SysReq(Print Screen) keys, type R E I S U B. R:  Switch to XLATE mode E:  Send Terminate
signal to all processes except for init I:  Send Kill signal to all processes except for init S:  Sync all mounted
filesystems U:  Remount filesystems as read-only B:  Reboot

REISUB is BUSIER backwards, as in "The System is busier than it should be", if you need to remember it. Or mnemonically

- R)eboot, E)ven, I)f, S)ystem, U)tterly, B)roken.


