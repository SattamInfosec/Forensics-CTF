# Forensics

##Tools used for solving Forensics challenges

### Image File

Try `file` comamnd on the image to learn more information.

To extract data inside Image files.

Try file carve using 'foremost <filename>' command. Foremost support all files. But it takes time to extract all file when you face a big size file.

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
pngcheck -cvt <FILE_NAME>.png
```
### Binwalk

Binwalk helps to find data inside the image or sometimes if binwalk reports as zip Archive, we can rename the file to <FILE_NAME>.zip to find interesting data.
```
> $ binwalk <IMAGE_NAME>
```

###Network Analysis

Used to analyze pcap or pcapng files

```
> $ wireshark <FILE_NAME>.pcapng
```
Aircrack-Ng tool: Crack 802.11 WEP and WPA-PSK keys
```
apt-get install aircrack-ng
```

###USB

[USBRip](https://github.com/snovvcrash/usbrip)-Simple CLI forensics tool for tracking USB device artifacts (history of USB events) on GNU/Linux

###Registry Viewers


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








### 7z Password Cracking

To extract 7z password, Use tool `7z2john`

### SSH Password Cracking

To crack encrypted ssh key use `ssh2john` tool