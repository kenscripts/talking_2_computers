# Table of Contents
* Moving Around
* Strings
* Data Wrangling
* Parsers

# Moving Around
* ls
   * [show only file name without file path](https://stackoverflow.com/questions/8518750/to-show-only-file-name-without-the-entire-directory-path)
   > `ls $DIRECTORY/* | xargs -n 1 basename`  
* dirname and basename
   * given file path, [dirname](https://stackoverflow.com/questions/6121091/how-to-get-a-file-directory-path-from-file-path) returns path of file
   * given file path, [basename](https://stackoverflow.com/questions/6121091/how-to-get-a-file-directory-path-from-file-path) returns name of file 

# Strings
* [concatenating strings]( https://linuxize.com/post/bash-concatenate-strings/)
   > `# string 1`\
   > `FIRSTNAME="Kenneth"`\
   > `# string 2`\
   > `LASTNAME="Acosta"`\
   > `# concatenate`\
   > `FULLNAME="$FIRSTNAME$LASTNAME"`\
* [slice string using specific character](https://stackoverflow.com/questions/4168371/how-can-i-remove-all-text-after-a-character-in-bash#:~:text=In%20Bash%20(and%20ksh%2C%20zsh,matching%20string%20will%20be%20removed.)
   > `# string variable`\
   > `MYNAME="Kenneth_Acosta"`\
   > `# get substring before underscore`\
   > `${MYNAME%_#}`\
   > `# get substring after underscore`\
   > `${MYNAME%_*}`
* [repeat a string n times](https://superuser.com/questions/86340/linux-command-to-repeat-a-string-n-times)
     > `# code to repeat string as long as file column` \
     > `TIMES=$(wc -l $FILE | cut -f1 -d" "` \
     > `yes "<string>" | head -n $TIMES`

# Data Wrangling
* cut
    * [a range of columns](https://stackoverflow.com/questions/4956873/how-to-cut-first-n-and-last-n-columns/51005303)
        > `# returns up to column 2`\
        >  `cut -f -2 $INPUT`\
        > `# returns everything after column 2`\
        > `cut -f 2- $INPUT`\
        > `# returns columns 2 to 4`\
        > `cut -f 2-4 $INPUT`
    * [split string and get n element](https://unix.stackexchange.com/questions/312280/split-string-by-delimiter-and-get-n-th-element/312400) 
        > `# returns the string "two"`\
        > `echo "one_two_three" | cut -d"_" -f2`
* sed
    * [use double-quotes to use shell variables within sed](https://askubuntu.com/questions/76808/how-do-i-use-variables-in-a-sed-command)
* awk
    * [converting float to integer](https://stackoverflow.com/questions/12929848/how-make-float-to-integer-in-awk)
    * [count columns in a file](https://stackoverflow.com/questions/8629330/unix-count-of-columns-in-file)
        > `# count number of fields; quit after 1st line`\
        > `awk -F"<delimiter>" {print NF; exit}' $INPUT`\
    * [return first instance of a variable](https://stackoverflow.com/questions/13581225/bash-output-the-line-with-highest-value)    
        > `awk '!seen[$1]++' $INPUT`
* grep
    * options
        > `-h = no filename`\
        > `-o = prints only the matching part of the line` \
        > `-m <n> = stop reading the file after n matches`

# Files
* [looping through lines in file](https://stackoverflow.com/questions/1521462/looping-through-the-content-of-a-file-in-bash)
* jq (json parser)
     * determine json structure
        > `# determine primary json keys`\
        > `jq -r 'keys' $JSON`\
        > `# determine keys within key`\
        > `jq -r '.<key> | keys' $JSON`
     * [converting json to tsv](https://stackoverflow.com/questions/48764829/jq-cannot-be-tsv-formatted-only-array-error)
        > `# turn original keys to key,value keys`\
        > `jq -r '.key | to_entries' $JSON` \
        > `# iterate through keys and values and generate lists` \
        > `jq -r '.key | to_entries | (map(.key),map(.value)) $JSON`\
        > `# convert lists to tsv`\
        > `jq -r '.key | to_entries | (map(.key),map(.value)) | @tsv' $JSON`
     * [display multiple keys from json](https://stackoverflow.com/questions/28164849/using-jq-to-parse-and-display-multiple-fields-in-a-json-serially)
        >`jq -r '.<key>[] | .<key 1> + "<delimiter>" + .<key 2>' $JSON`
     * [filter keys containing string](https://stackoverflow.com/questions/51869431/using-jq-select-elements-with-keys-containing-some-string-key-preserved-in-resu)
        >`jq -r '.<key> | select (.<key> | contains("<string>"))' $JSON`
     * [filter keys based on value](https://stackoverflow.com/questions/18592173/select-objects-based-on-value-of-variable-in-object-using-jq)
        >`jq -r '.<key> | select(.<filter key> == <value>) | .<desired key>' $JSON`
