# Linux for Beginners by Jason Cannon

> $ normal user , # superuser.  

> Brackets [] meaning are optional.

> If you execute `cd` without specifying a directory, cd changes the current directory to your home directory.  

> `exit`, `logout`, or `Ctrl-d` - Exits the shell or your current session.  

`which <commandName>`  to see command path.  

`cd -` to navigate previous working directory.  

`mkdir [-p] directory` - Create a directory. Use the -p (parents) option to create intermediate directories.  

`rm -rf directory` Recursively removes the directory and all files and directories in that directory structure.

> When you use the -F option for ls a character is appended to the file name that reveals what type it is.

`ls -lF`

> / Directory.  
> @ Link. The file that follows the -> symbol is the target of the link.  
> * Executable program.  

`ls -latr` sort them by time, but in reverse order.  
`ls -R` to see all directory and files.  
`tree` List content of directories in a tree-like format.  
`tree -d`  List directories only.  

`groups <groupName>` to see users of specific group.  

> `chmod` The change mode command.

> ugoa The user category. One or more of u for user, g for group, o for other, a for all.

> +-= One of +, -, or =. Use + to add permissions, - to subtract them, or = to explicitly set them.  

> rwx The permissions. One or more of r for read, w for write, and x for execute.  

> you can give permissions with numeric too.

#### Examples for chmod

`chmod g+w sales.data`  
`chmod g+wx sales.data`  
`chmod u=rwx,g+x sales.data`  
`chmod a=r` then only read will be available regardless of any existing permissions. Result : -r--r--r--  
`chmod u=rwx,g=rx,o=` Result : -rwxr-x---  

**If you are sure a file's permissions have been set correctly, look at the parent directory.**
`ls -ld` to see current directory permission.  

`umask <octalNumber>` to set umask.  
`umask -S` to see default umask settings.  

[Ubuntu ACL Documentation](https://help.ubuntu.com/community/FilePermissionsACLs)

`find` it find all files in the current directory.
`find -name <filename>` Displays files whose name matches pattern. This is case sensitive.
`find -iname <filename>` Same as -name, but ignores case.
`find -mtime num_days` Finds files that are num_days old.
`find  -newer file` Finds files that are newer than file.

#### Examples for find
`find /usr/local -name *conf`  
`find . -mtime +10 -mtime -13`  
`find . -name "s*" -ls`  
`find . -size +300M`  
`find . -type d -newer b.txt`  

> `locate` is faster option for find.  

`cat file`  Display the entire contents of file.  
`more file` Browse through a text file. Press the Spacebar to advance to the next page.  

> By default head and tail only display ten lines.  
`head -2 file.txt` 

`sdiff file1 file2` or `vimdiff file1 file2` Compare two files side by side.

`file test` to see file type.  

`grep username test.txt` to search username.  
`grep -v username test.txt` not matched lines. 
`grep -i name test.txt` ignoring case.  
`grep -c` count the number.  
`grep -n` Precede output with line numbers from the file.  

`strings file` Display printable strings in binary files.  

`strings BlueTrain.mp3 | grep -i john | head -1 | cut -d ' ' -f 2` space as the delimiter (-d ' ') , second field (-f 2)  

`grep bob /etc/passwd | cut -f1,5 -d: | sort` 

`sed 's/unix/linux/' linux.txt` to change unix with linux.  
`sed 's/unix/linux/g' linux.txt` to change all words.  

`grep bob /etc/passwd d: | sort | sed 's/:/ /' | column -t`  to see columns nicely.

`cp source_file destination_file` 
`cp source_file1 [source_fileN ...] destination_directory` Copy source_files to destination_directory.  

`cp -i source_file destination_file` If the destination_file exists, cp will prompt you before it overwrites the file.  

`cp -r source_directory destination` Copy source_directory recursively to destination. If destination exists, copy source_directory into destination, otherwise create destination with the contents of directory.  

`mv -i source destination` Run mv in interactive mode. If the destination exists, mv will prompt you before it overwrites the file.  

`sort file` - Sort text in file.  
`sort -k F file` Sort by key. The F following -k is the field number.  
`sort -r file` - Sort in reverse order.  
`sort -u file` - Sort text in file, removing duplicate lines.  

`tar [-] c|x|t f tarfile [pattern]` Create, extract or list contents of a tar archive using pattern, if supplied.  

>> c - Create a tar archive.  
>> x - Extract files from the archive.  
>> t - Display the table of contents (list).  
>> v - Causes tar to be verbose.  
>> f file - The tar archive file to perform operations against.  

`gzip file` - Compress file. The resulting compressed file is named file.gz.  
`gunzip file` - Uncompress files.  
`gzcat` or `zcat` - Concatenates and prints compressed files.  

`du -h`- Display sizes in human readable format.  

> Use the greater-than sign (>) to redirect output and the less-than sign (<) to redirect input.  

`sort < files.txt`  
`sort < files.txt > sorted_files.txt`  

> To redirect the error messages you had to explicitly specify file descriptor 2 with 2>  

`ls here not-here 2> out.err`  

> If you want to capture both standard output and standard error, use 2>&1.  

`ls here not-here > out.both 2>&1`  
`cat sample.txt &> out` short way  
`command 2> error.txt 1> output.txt` to send different file. 
> /dev/null - Redirect output to nowhere
`ls here not-here 2> /dev/null` ouf terminal result : here  
`ls here not-here > /dev/null 2>&1` you cannot see anything in your terminal.  

