# Serial
Uploading files over serial
http://www.tldp.org/HOWTO/Remote-Serial-Console-HOWTO/upload.html

minicom default settings
baud: 115200 8N1, flow control: N
# minicom
setup
sudo minicom -s

Example:
CTRL-A Z for help | 115200 8N1 | NOR | Minicom 2.7 | VT102 | Offline | ttyUSB1

Notes:
- If the serial is messed up, it might be multiple processes. Try killing
  sudo fuser -a /dev/ttyUSB1
  kill thepid
- If exiting uncleaning, the lock might be held. rm /var/lock/LCK..ttyUSB1
