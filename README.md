# Notes on basic concepts of unix, shell, etc https://www.youtube.com/watch?v=U3iNcBtycaQ&list=PLUQy4zfrctjH-FsjpIZDZ0NBznvF4FdNP&index=1

# Shows us contents within current path
ls

# Flag denotes file type 
ls -F 

# For relative path
ls -F example

# For absolute path from root
ls -F /example

# Relay current path
pwd

# Changes the shell's idea of which directory in
cd example_directory

# Change to the parent directory
cd ..

# Displays all directories including those begining . or ..
ls -F -a

# \ is different in different systems

# This denotes a space when referring to a file
my\ files.txt

# On windows

# Directory
C:\Users\example

# Try to avoid special characters 

# Windows is case insensitive

# Make a new directory
mkdir temp

# Make a plain text file
nano junk

# Size of files in disk blocks
ls -s

# Sizes in bytes
ls -s -h

# Remove files, no un-delete
rm junk

# Remove directory, but only if empty
rmdir temp

# Change file name by moving
mv temp/junk tmp/quotes.txt

# Move file to a new directory
mv temp/quotes.txt .

# Copy
cp quotes.text temp/quotations.txt

# Copy with original name
cp temp/quotes.text .

