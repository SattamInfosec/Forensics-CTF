# Forensics

### Tools used for solving Forensics challenges

### Image File

Try `file` comamnd on the image to learn more information.

To extract data inside Image files.



```
> $ zsteg <FILE_NAME>
```

To check for metadata of the Image files.

```
> $ exiftool <FILE_NAME>
```

To search for particular string or flag in an Image file.

```
> $ strings <FILE_NAME> | grep flag{
```

To extract data hidden inside an image file protected with password.

```
> $ steghide extract -sf <FILE_NAME>
```
Verifies the integrity of PNG and dump all of the chunk-level information in human-readable form
```
> $pngcheck -cvt <FILE_NAME>.png
```
### Binwalk

Binwalk helps to find data inside the image or sometimes if binwalk reports as zip Archive, we can rename the file to <FILE_NAME>.zip to find interesting data.
```
> $ binwalk <IMAGE_NAME>
```

### File Carving

process used in computer forensics to extract data from a disk drive or other storage device without the assistance of the file system that originality created the file

[dd](https://man7.org/linux/man-pages/man1/dd.1.html) - Copy a file, converting and formatting according to the operands.

Try file carve using `foremost <filename>` command. Foremost support all files. But it takes time to extract all file when you face a big size file.

[HXD](https://mh-nexus.de/en/hxd/) - user-friendly hex editor that allows you to perform low-level editing and modifying of a raw disk or main memory (RAM)

### Network Analysis

Used to analyze pcap or pcapng files

```
> $ wireshark <FILE_NAME>.pcapng
```

[NetworkMiner](https://www.netresec.com/index.ashx?page=NetworkMiner) -  Network Forensic Analysis Tool used as a passive network sniffer/packet capturing tool in order to detect operating systems, sessions, hostnames, open ports

[Aircrack-NG Tool](https://www.aircrack-ng.org/) - Crack 802.11 WEP and WPA-PSK keys
```
apt-get install aircrack-ng
```

### USB

[USBRip](https://github.com/snovvcrash/usbrip) - Simple CLI forensics tool for tracking USB device artifacts (history of USB events) on GNU/Linux

### Registry Viewers

[OfflineRegistry View](https://www.nirsoft.net/utils/offline_registry_view.html) - Simple tool for Windows that allows you to read offline Registry files from external drive and view the desired Registry key in .reg file format.

[Registry Viewer](https://accessdata.com/product-download/registry-viewer-2-0-0) - Used to view Windows registries.

### Extract NTFS Filesystem

```
If there is ntfs file, extract with 7Zip on Windowds. 
If there is a file with alternative data strems, we can use the command `dir /R <FILE_NAME>`.
Then we can this command to extract data inside it `cat <HIDDEN_STREAM> > asdf.<FILE_TYPE>`
```

To extract ntfs file system on Linux.

```
> $ sudo mount -o loop <FILENAME.ntfs> mnt
```

### Recover Files from Deleted File Systems

To Recover Files from Deleted File Systems from Remote Hosts.
```
> $ ssh username@remote_address "sudo dcfldd -if=/dev/sdb | gzip -1 ." | dcfldd of=extract.dd.gz
> $ gunzip -d extract.dd.gz
> $ binwalk -Me extract.dd
```

### Memory Forensics 

Tool for investigate memory dump


[volatility](https://github.com/volatilityfoundation/volatility) - extraction of digital artifacts from volatile memory (RAM) samples

[WindowsSCOPE](http://www.windowsscope.com/) - which enables memory forensics for Windows computers

### Audio forensics

To Extract Data from Audio File 


[Audacity](https://sourceforge.net/projects/audacity/) -  checking integrity, improving speech clarity, transcribing dialogue





### Zip Password Cracking

To extract ZIP password, Use tool `fcrackzip` OR `zip2john`

```
> $zip2john <File-Name>.zip > <Name>.txt

> $john <Name>.txt --wordlist=/usr/share/wordlists/rockyou.txt
```
### Rar Password Cracking 

To extract Rar password, Use tool `rar2john`

```
> $rar2john <File-Name>.rar > <Name>.txt

> $john <Name>.txt --wordlist=/usr/share/wordlists/rockyou.txt

```

### Pdf Password Cracking 

To extract Pdf password, use tool `pdf2john`

```
> $pdf2john <File-Name>.pdf > <Name>.txt

> $john <Name>.txt --wordlist=/usr/share/wordlists/rockyou.txt

```

### 7z Password Cracking

To extract 7z password, Use tool `7z2john`

```
> $7z2john <File-Name>.7z > <Name>.7z

> $john id_rsa.txt --wordlist=/usr/share/wordlists/rockyou.txt

```

### SSH Password Cracking

To crack encrypted ssh key use `ssh2john` tool

```
> $ssh2john id_rsa > id_rsa.txt

> $john id_rsa.txt --wordlist=/usr/share/wordlists/rockyou.txt

> $ssh -i id_rsa <Username>@<IP-Address>
   :Enter the Password Cracked 
```