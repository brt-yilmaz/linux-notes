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

> By default head and tai`l only display ten lines.  
`head -2 file.txt` 

`sdiff file1 file2` or `vimdiff file1 file2` Compare two files side by side.





