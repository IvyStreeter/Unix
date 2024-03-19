Notes on basic concepts of unix, shell, etc https://www.youtube.com/watch?v=U3iNcBtycaQ&list=PLUQy4zfrctjH-FsjpIZDZ0NBznvF4FdNP&index=1

No Notes for episode 1.

# Episode 2: Files and Directories 

Checks current user
```
whoami
```

Shows us contents within current path
```
ls
```

Flag denotes file type 

```
ls -F 
```

For relative path
```
ls -F example
```

For absolute path from root
```
ls -F /example
```

# Episode 3: Creating and Deleting 

Relay current path
```
pwd
```

Changes the shell's idea of which directory in
```
cd example_directory
```

Change to the parent directory
```
cd ..
```

Displays all directories including those begining . or ..
```
ls -F -a
```

\ is different in different systems

This denotes a space when referring to a file
```
my\ files.txt
```

On windows

Directory
```
C:\Users\example
```

Try to avoid special characters 

Windows is case insensitive

Make a new directory
```
mkdir temp
```

Make a plain text file
```
nano junk
```

Size of files in disk blocks
```
ls -s
```

Sizes in bytes
```
ls -s -h
```

Remove files, no un-delete
```
rm junk
```

Remove directory, but only if empty
```
rmdir temp
```

Change file name by moving
```
mv temp/junk tmp/quotes.txt
```

Move file to a new directory
```
mv temp/quotes.txt .
```

Copy
```
cp quotes.text temp/quotations.txt
```

Copy with original name
```
cp temp/quotes.text .
```

# Episode 4: Pipes and Filters 

count words of all files with a particular filetype
```
wc *.fileextension
```

If you want to look through the files and find the largest

specify lines and length, this puts all information into a file
```
wc -l *.fileextension > lengths
```

if multiple files, we can concat
```
cat lengths
```

this does not change the file, but prints the sorted list 
```
sort lengths
```

can place the sorted lines into a new file like before by using the >
```
sort lengths > sorted-lengths
```

can use the command head to give the number of lines from the top of the file to print, the argument -1 to display the top line
```
head -1 sorted-lengths
```

by using pipe ,|, you can use the output of the left as the input to the right. This removes the intermediate files that were created earlier This concept is useful in R.
```
sort lengths | head -1
```

we can also use pipe to remove the creation of the lengths file
```
we -l *.fileextension | sort lengths | head -1
```

This programming model that takes a standard input and redirects the standard output to another process is called pipes and filters. It is encouraged to write Unix in pipes and filters for legibility and conciseness 

# Episode 5: Permissions 

Computers have users, groups, and all as different categories of things that can read, write, or excute a file.

How can we view executable files? Files with a * will be executable.
```
ls -F
```

Who can see, change, or run programs? 
We can view the permissions using the -l flag
```
ls -l
```
* The list is written in this order: file permissions (read, write, or execute), 1 (not discussed), name of the user that owns the file, id of the group that owns the file, size in bytes ,times the file was last modified, name of the file
* -rw-rw-r-- gives us information regarding user/group/everyone else and what they can do to the file
* r is read, w is write, x is execute, - is off

* the first character gives us file type, - for file, d for directory
* the next 3 letters tells us user owner permissions
* the next 3 gives group permissions
* the last 3 is everyone else 
* to see long form permissions for . and ..
```
ls -a -l
```
* The directory and it's parent start with a d.

You may see an x for a directory, what does this mean?
execute for directory allows user to transverse the directory, but not look at the contents.

to change permissions, change mode is used (chmod)
let's change the user to only read and write
```
chmod u=rw file.grd
```

let's change the group to only r
we can place 2 commands together as long as they are separated with a ;
```
chmod g=r; ls -l file.grd
```

let's change everyone else to have no permissions
```
chmod a= file.grd; ls -l file.grd
```

Windows is different from Unix
Windows permissions is defined by Acess Control Lists (ACLs)
An ACL is a list of pairs (who, what)
You can give userA permission append data to a file without read/delete
You can give userB permission to delete files without being able to append/read
This is more flexible, but harder to read/understand

## Creating our own commands 
this appends cat to the file smallest
```
cat > smallest
```

This pipe finds the smallest file, using Ctrl-D means end of input on Unix. Similarly, Ctrl-Z does the same in Windows
```
wc -l *.pdb | sort | head -1
^D 
```

To run the program, first lets add execute to user to this file (without changing anything else)
(alternatively, - can be used to subtract permissions)
```
chmod u+x smallest
```

Now we can run this file, but only in the current working directory.
```
./smallest
```

# Episode 6: find things in files and themselves

grep: global/regular expression/print
grep finds and prints lines in a file that match a pattern

This will return lines containing the word 'not'
```
grep not file.txt
```

This creates a word boundary so that only lines with the word day are printed.
```
grep -w day file.txt
```

This numbers the lines that match the search
```
grep -n it file.txt
```

Combine the commands
```
grep -w -n it file.txt
```
