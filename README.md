# Notes on basic concepts of unix, shell, etc https://www.youtube.com/watch?v=U3iNcBtycaQ&list=PLUQy4zfrctjH-FsjpIZDZ0NBznvF4FdNP&index=1

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

Who can see, change, run programs? 
We can view the permissions using the ```
-l flag
ls -l
```

* -rw-rw-r-- gives us information regarding user/group/everyone else and what they can do to the file
* r is read, w is write, x is execute, - is off
* the first character gives us file type, - for file, d for directory
* the next 3 letters tells us user owner permissions
* the next 3 gives group permissions, 
* the last 3 is everyone else 
* to see long form permissions for . and ..
```
ls -a -l
```

execute for directory allows user to transverse the notes

to change permissions, change mode is used (chmod)

