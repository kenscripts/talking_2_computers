Things related to the Linux operating system.

# Table of Contents
  * File System
  * Operations
  * Commands
  
# File System
  * [key directories](https://www.dummies.com/computers/operating-systems/linux/linux-file-system-basics/)

# Operations
 * [chroot](https://en.wikipedia.org/wiki/Chroot)

# Commands
### Moving Around
 * dirname and basename
    * given file path, [dirname](https://stackoverflow.com/questions/6121091/how-to-get-a-file-directory-path-from-file-path) returns path of file
    * given file path, [basename](https://stackoverflow.com/questions/6121091/how-to-get-a-file-directory-path-from-file-path) returns name of file 
### Data Wrangling
 * cut
     * [a range of columns](https://stackoverflow.com/questions/4956873/how-to-cut-first-n-and-last-n-columns/51005303)
        > `# returns up to column 2`\
        >  `cut -f -2 $FILE`\
        > `# returns everything after column 2`\
        > `cut -f 2- $FILE`\
        > `# returns columns 2 to 4`\
        > `cut -f 2-4 $FILE`\
     * [split string and get n element](https://unix.stackexchange.com/questions/312280/split-string-by-delimiter-and-get-n-th-element/312400) 
        > `# returns the string "two"`\
        > `echo "one_two_three" | cut -d"_" -f2 
