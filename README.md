# Linux Commands
LINUX IS CASE SENSITIVE

## CURRENT USER ID
	whoami

## SUPER USER PERMISSION
COMMAND | DESCRIPTION
------------ | -------------
sudo | sudo is meant to run a single command with root privileges
sudo su | su it prompts you for the password of the current user. 

By default, Ubuntu "remembers" your password for 15 minutes, so that you don't have to type your password every time.

## ADD NEW USER OR GROUP
sudo adduser [username]
sudo addgroup [groupname]

## OWNERS
USER| GROUP | ALL | OTHER
------------ | ------------- | ------------- | -------------
u | g | a | o

## PERMISSION
read(r) | write(w) | execute(x)
------------ | ------------- | -------------
0 | No Permission | ---
1 | Execute | --x
2 | Write | -w-
3 | Execute + Write | -wx
4 | Read | r--
5 | Read + Execute | r-x
6 | Read +Write | rw-
7 | Read + Write +Execute | rwx

## ERROR REDIRECTION

Whenever you execute a program/command at the terminal, 3 files are always open, viz., standard input, standard output, standard error.

File | Descriptor
------------ | -------------
Standard Input STDIN | 0
Standard Output STDOUT | 1
Standard Error STDERR | 2

## SYMBOL MEANING
<table>
	<tr>
    		<th><b>SYMBOL</b></th>
    		<th><b>Descriptor</b></th>
  	</tr>
  	<tr>
    		<td>~#</td>
    		<td>symbol for root user</td>
  	</tr>
  	<tr>
    		<td>~$</td>
    		<td>symbol for regular user</td>
  	</tr>
  	<tr>
    		<td>></td>
    		<td>
			symbol for output (STDOUT) redirection <br>
      			<b>Example 1)</b><br>
      			ls -al > listing_output <br> 
      			cat listing_output to view file  <br>
      			<b>Example 2)</b><br>
      			cat music.mp3 > /dev/audio
    		</td>
  	</tr>
  	<tr>
    		<td>2></td>
    		<td>
			re-direct the error output to a file named "errorfile"<br>
			<b>Example 1)</b><br>
			ls -al 2> error_output.log
		</td>
  	</tr>
	<tr>
		<td>>&</td>
		<td>
			re-directs output of one file to another.<br>
			<b>Example 1)</b><br>
			ls Documents ABC> dirlist 2>&1<br>
			which writes the output from one file to the input of another file.<br>
			2>&1 means that STDERR redirects to the target of STDOUT (which is the file dirlist)<br>
			We are redirecting error output to standard output which in turn is being re-directed to file dirlist.<br>
			Hence, both the output is written to file dirlist
		</td>
	</tr>
</table>


## DIRECTORY
COMMAND | DESCRIPTOR
------------ | -------------
pwd | Current Directory
cd dir_name | Change Directory
cd .. | Change Directory (one step backward to current directory)
cd ~ | Change Directory to Home
cd / | Change Directory to Root

## LISTING FILES
```linux
ls [option(s)] [file(s)]
```
COMMAND | DESCRIPTOR
------------ | -------------
-R | SUBDIRECTORIES LIST
-a | HIDDEN FILES
-l | DETAILED LIST
-t | SORTING BY TIME

COMMAND | DESCRIPTOR
------------ | -------------
more [options] filename	| Output the contents of the file
head [options] filename	| Output the first 10 lines of the file
tail [options] filename	| Output the last 10 lines of the file

tail -f [filename] Output the contents of file as it grows,starting with the last 10 lines

## CHANGE PERMISSION
```bash
chmod [options] mode file(s)
```
The mode parameter has three parts: group, access, and access type. 
1) group accepts the following characters:	user(u), group(g), all(a), others(o)
2) access is granted by the + symbol and denied by the - symbol. 
3) access type is controlled by the following options:	read(r), write(w), execute(x) OR uid bit


## CREATE FOLDER/ DIRECTORY
```bash
mkdir [option(s)] directoryname(s)
```

## REMOVE FOLDER/ DIRECTORY
```bash
rmdir [option(s)] directoryname(s)
```

## MOVE/ RENAME FILE/ FOLDER
```bash
mv [option(s)] sourcefile location
```
COMMAND | DESCRIPTOR
------------ | -------------
-b | Creates a backup copy of the sourcefile before moving
-i | Waits for confirmation, if necessary, before an existing targetfile is overwritten

## REMOVE FILE
```bash
rm [option(s)] file(s)
```
COMMAND | DESCRIPTOR
------------ | -------------
-r | Deletes any existing subdirectories
-f | Force to remove the file
-i | Waits for confirmation before deleting each file.

## COPY FILE
```bash
cp [option(s)] sourcefile location
```
COMMAND | DESCRIPTOR
------------ | -------------
-i | Waits for confirmation, if necessary, before an existing targetfile is overwritten
-r | Copies recursively (includes subdirectories)

## CREATE A FILE OR UPDATE PREVIOUS FILE WITH SAME NAME
```bash
touch filename
```
OR
```bash
cat > filename
```

1. Touch:
If file is already existing, it will update the time stamp.
If the file does not exist, then 'touch file_name' creates a new file with 0 KB file size.

2. Cat:
Dumps the contents of the file to the standard output , if no options specified.
Cat command help to create the file in writable format. once you write cat > file name it will allow you to type the text, enter ctrl+d to save and exit. if you will check  with the commant cat filename it will show the content of the file


## VIEW A FILE
```bash
cat filename
```

## COMBINE 2 FILE
```bash
cat file1 file 2 > file3
```

## COMPRESS A FILE
```bash
gzip [parameters] file(s)
```
COMMAND | DESCRIPTOR
------------ | -------------
-d | decompresses the packed gzip files so they return to their original size and can be processed normally (like the command gunzip).

## COMPRESS DIRECTORY
```bash
tar options archive file(s)
```
COMMAND | DESCRIPTOR
------------ | -------------
-f | Writes the output to a file and not to the screen as is usually the case
-c | Creates a new tar archive
-r | Adds files to an existing archive
-t | Outputs the contents of an archive
-u | Adds files, but only if they are newer than the files already contained in the archive
-x | Unpacks files from an archive (extraction)
-z | Packs the resulting archive with gzip
-j | Compresses the resulting archive with bzip2
-v | Lists files processed

## FIND A FILE IN GIVEN DIRECTORY
```bash
find [option(s)]
```
The find command allows you to search for a file in a given directory. 
The first argument specifies the directory in which to start the search. 
The option -name must be followed by a search string, which may also include wild cards. 
Unlike locate, which uses a database, find scans the actual directory.

## COMMANDS TO ACCESS FILE CONTENT
```bash
cat [option(s)] file(s)
```
The cat command displays the contents of a file, printing the entire contents to the screen without interruption.

COMMAND | DESCRIPTOR
------------ | -------------
-n | Numbers the output on the left margin

```bash
less [option(s)] file(s)
```
This command can be used to browse the contents of the specified file. Scroll half a screen page up or down with PgUp and PgDn or a full screen page down with Space. Jump to the beginning or end of a file using Home and End. Press Q to exit the program.
```bash
diff [option(s)] file1 file2
```
The diff command compares the contents of any two files. The output produced by the program lists all lines that do not match.
This is frequently used by programmers who need only send their program alterations and not the entire source code.
	
COMMAND | DESCRIPTOR
------------ | -------------
-q | Only reports whether the two given files differ
```bash
grep [option(s)] searchstring filenames
```
The grep command finds a specific searchstring in the specified file(s). If the search string is found, the command displays the line in which the searchstring was found along with the file name.

COMMAND | DESCRIPTOR
------------ | -------------
-i | Ignores case
-l | Only displays the names of the respective files, but not the text lines
-n | Additionally displays the numbers of the lines in which it found a hit
-l | Only lists the files in which searchstring does not occur
	
<table>
	<tr>
		<th>COMMAND</th>
		<th>DESCRIPTOR</th>
	</tr>
	<tr>
		<td>.</td>
		<td>replaces any character</td>
	</tr>
	<tr>
		<td>^</td>
		<td>matches start of string</td>
	</tr>
	<tr>
		<td>$</td>
		<td>matches end of string</td>
	</tr>
	<tr>
		<td>*</td>
		<td>matches up zero or more times the preceding character</td>
	</tr>
	<tr>
		<td>\</td>
		<td>Represent special characters</td>
	</tr>
	<tr>
		<td>()</td>
		<td>Groups regular expressions</td>
	</tr>
	<tr>
		<td>?</td>
		<td>Matches up exactly one character </td>
	</tr>
	<tr>
		<td>{n}</td>
		<td>Matches the preceding character appearing 'n' times exactly</td>
	</tr>
	<tr>
		<td>{n,m}</td>
		<td>Matches the preceding character appearing 'n' times but not more than m</td>
	</tr>
	<tr>
		<td>{n, }</td>
		<td>Matches the preceding character only when it appears 'n' times or more </td>
	</tr>
	<tr>
		<td>\+</td>
		<td>Matches one or more occurrence of the previous character</td>
	</tr>
	<tr>
		<td>\?</td>
		<td>Matches zero or one occurrence of the previous character </td>
	</tr>
</table>




## HISTORY OF COMMANDS
history


## CLEAR COMMAND HISTORY
clear


## PIPING
Piping, represented by the pipe character "|", is used to combine two or more commands together. The output of the first command serves as input the next command, and so on.


## SYSTEM INFORMATION
```bash
df [option(s)] [directory]
```
The df (disk free) command, when used without any options, displays information about the total disk space, the disk space currently in use, and the free space on all the mounted drives. If a directory is specified, the information is limited to the drive on which that directory is located.

COMMAND | DESCRIPTOR
------------ | -------------
-H | shows the number of occupied blocks in gigabytes, megabytes, or kilobytes — in human-readable format
-t | Type of file system (ext2, nfs, etc.)
```bash
du [option(s)] [path]
```
This command, when executed without any parameters, shows the total disk space occupied by files and subdirectories in the current directory.

COMMAND | DESCRIPTOR
------------ | -------------
-a | Displays the size of each individual file
-h | Output in human-readable form
-s | Displays only the calculated total size
```bash
free [option(s)]
```
The command free displays information about RAM and swap space usage, showing the total and the used amount in both categories.

COMMAND | DESCRIPTOR
------------ | -------------
-b | Output in bytes
-k | Output in kilobytes
-m | Output in megabytes
```bash
date [option(s)]
```
This simple program displays the current system time. If run as root, it can also be used to change the system time. Details about the program are available in date.
```bash
uptime
```
Show current uptime



## PROCESSES
```bash
top [options(s)]
```
top provides a quick overview of the currently running processes. Press H to access a page that briefly explains the main options to customize the program.
```bash
ps [option(s)] [process ID]
```
If run without any options, this command displays a table of all your own programs or processes — those you started. The options for this command are not preceded by hyphen.
```bash
aux
```
Displays a detailed list of all processes, independent of the owner.
```bash
kill [option(s)] process ID
```
Unfortunately, sometimes a program cannot be terminated in the normal way. However, in most cases, you should still be able to stop such a runaway program by executing the kill command, specifying the respective process ID (see top and ps).
kill sends a TERM signal that instructs the program to shut itself down. If this does not help, the following parameter can be used:
COMMAND | DESCRIPTOR
------------ | -------------
-9 | Sends a KILL signal instead of a TERM signal, with which the process really is annihilated by the operating system. This brings the specific processes to an end in almost all cases.
```bash
killall [option(s)] processname
```
This command is similar to kill, but uses the process name (instead of the process ID) as an argument, causing all processes with that name to be killed.

<table>
	<tr>
		<th>COMMAND</th>
		<th>DESCRIPTOR</th>
	</tr>
	<tr>
		<td>ps aux | grep 'telnet'</td>
		<td>displays all process ids related to telnet process</td>
	</tr>
	<tr>
		<td>ps aux | less</td>
		<td>display all running process</td>
	</tr>
	<tr>
		<td>ps aux | less</td>
		<td>display all running process</td>
	</tr>
	<tr>
		<td>ps -U root -u root -N</td>
		<td>see every process except those running as root</td>
	</tr>
	<tr>
		<td>ps -U root -u root --deselect</td>
		<td>see every process except those running as root</td>
	</tr>
	<tr>
		<td>ps -u username</td>
		<td>See process run by given username</td>
	</tr>
</table>



## NETWORK
```bash
ping [option(s)] host name|IP address
```
The ping command is the standard tool for testing the basic functionality of TCP/IP networks. It sends a small data packet to the destination host, requesting an immediate reply. If this works, ping displays a message to that effect, which indicates that the network link is basically functioning.

COMMAND | DESCRIPTOR
------------ | -------------
-c | number Determines the total number of packages to send and ends after they have been dispatched. By default, there is no limitation set.
-f | flood ping: sends as many data packages as possible. A popular means, reserved to root, to test networks.
-i | value Specifies the interval between two data packages in seconds. Default: one second
```bash
nslookup
```
The Domain Name System resolves domain names to IP addresses. With this tool, send queries to information servers (DNS servers).





## INSATLL SOFTWARE
```bash
sudo apt-get install packagename
```
## UPDATE ALL SOFTWARE
```bash
sudo apt-get update
```
## Launching the CLI on Ubuntu
Go to the Dash and type terminal 
Or
You can press CTRL + Alt + T to launch the Terminal 
