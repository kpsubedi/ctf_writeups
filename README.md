# ctf_writeups

Description 


WriteUp
Find the type of file

<strong>root@kali:~/polictf/forensic/john-in-the-middle/new_way# file john-in-the-middle.pcap </strong> 


john-in-the-middle.pcap: tcpdump capture file (little-endian) - version 2.4 (Ethernet, capture length 262144)


root@kali:~/polictf/forensic/john-in-the-middle/new_way/output# foremost -h


foremost version 1.5.7 by Jesse Kornblum, Kris Kendall, and Nick Mikus.
$ foremost [-v|-V|-h|-T|-Q|-q|-a|-w-d] [-t <type>] [-s <blocks>] [-k <size>] 
	[-b <size>] [-c <file>] [-o <dir>] [-i <file] 

-V  - display copyright information and exit
-t  - specify file type.  (-t jpeg,pdf ...) 
-d  - turn on indirect block detection (for UNIX file-systems) 
-i  - specify input file (default is stdin) 
-a  - Write all headers, perform no error detection (corrupted files) 
-w  - Only write the audit file, do not write any detected files to the disk 
-o  - set output directory (defaults to output)
-c  - set configuration file to use (defaults to foremost.conf)
-q  - enables quick mode. Search are performed on 512 byte boundaries.
-Q  - enables quiet mode. Suppress output messages. 
-v  - verbose mode. Logs all messages to screen

root@kali:~/polictf/forensic/john-in-the-middle/new_way# foremost john-in-the-middle.pcap 

Processing: john-in-the-middle.pcap
|*|

root@kali:~/polictf/forensic/john-in-the-middle/new_way# ls 

john-in-the-middle.pcap  output

root@kali:~/polictf/forensic/john-in-the-middle/new_way# tree .

.
├── john-in-the-middle.pcap
└── output
    ├── audit.txt
    └── png
        ├── 00000308.png
        ├── 00000403.png
        ├── 00000644.png
        ├── 00000650.png
        └── 00000656.png

2 directories, 7 files

root@kali:~/polictf/forensic/john-in-the-middle/new_way/output/png# ls
00000308.png  00000403.png  00000644.png  00000650.png  00000656.png



root@kali:~/polictf/forensic/john-in-the-middle/new_way/output/png# convert 00000308.png -edge 10 00000308_new.png 


Flag:
root@kali:~/polictf/forensic/john-in-the-middle/new_way/output/png# eog 00000308_new.png

flag{J0hn_th3_Sn1ff3r}










