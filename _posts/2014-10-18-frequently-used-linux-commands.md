---
layout: post
title: "Frequently Used Linux Commands"
categories:
tags: "Linux"
---

### Frequently Used

#### Execute a command without saving it in the history
```bash
<space>command
``` 
#### Execute the last command with sudo  
```bash
sudo !!
```
#### Last argument of the last command
```bash
!$
# Example
mkdir /tmp/abcd
cd !$
echo $(pwd) # will print "/tmp/abcd"   
```

#### Put a command into history without execute it
```bash  
# alt + # (alt + shift + #) 
```

#### Runs previous command but replacing
```bash
^foo^bar # replace "foo" with "bar" in previous command
```

#### Execute a command at a given time
```bash
echo "ls -l" | at midnight
# OR
at midnight<<<'ls -l'
```

#### Get the external IP address 
```bash
curl ifconfig.me
```

#### Mount folder/filesystem through SSH
```bash
sshfs name@server:/path/to/folder /path/to/mount/point
```

#### Mount a temporary ram partition
```bash
mount -t tmpfs tmpfs /mnt -o size=1024m
```

#### Create a SSH tunnel
```bash
ssh -N -L2001:localhost:80 somemachine
# start a tunnel from some machine's port 80 to your local post 2001
```

#### Run a command and  redirect stderr and stdout to a file
```
command > a.log 2>&1 &
```


### sort

```bash
-b, --ignore-leading-blanks # Ignore leading blanks
-f, --ignore-case # Fold lowercase to upper case to sort
-i, --ignore-nonprinting # Consider only printable characters
-h, --human-numeric-sort # compare human readable numbers (e.g., 2K 1G)
-r, --reverse # Reverse the result of comparisons
-n, --numeric-sort # Compare according to string numerical value
-R, --random-sort # Sort by random hash of keys
-o, --output=FILE # Write result to FILE instead of standard output
```

Sort by field options:

```bash
-t, --field-separator=SEP #Use SEP instead of non-blank to blank transition
-k, --key=KEYDEF # Sort via a key; KEYDEF gives location and type
    # KEYDEF  is F[.C][OPTS][,F[.C][OPTS]] for start and stop position, 
    # where F is a field number and C a character position in the field; 
    # both are ori‐ gin 1, and the stop position defaults to the line's end.  
```

Examples:

Input, cat.txt
```
Solaris,10
Linux,20
AIX,25
Linux,25
Unix,30
HPUX,100
```

```bash
cat cat.txt | sort -n  # Sort cat.txt using numeric-sort
cat cat.txt | sort -t"," -k2,2nr 
        # Sort cat.txt by the second field, 
        # numeric-sort and in reversed order, fields are separated by ","
```


### tar



### join

### cut
Print selected parts of lines from each FILE to standard output. Options:

```bash
-d, --delimiter=DELIM # Use DELIM instead of TAB for field delimiter
-f, --fields=LIST # Select only these fields; 
                  # also print any line that contains no delimiter character, 
                  # unless the -s option is specified
-s, --only-delimited # Do not print lines not containing delimiters

# Examples:

cut -f1,3 cat.txt ## Extact the 1st and the 3rd columns
cut -d"," -f1,2 cat.txt ## Extract the 1st and the 3rd fields, fields are separated by ","
```

### uniq
Filter adjacent matching lines from INPUT (or standard input), writing to OUTPUT (or standard output). Options:

```bash
# With no options,  matching lines are merged to the first occurrence
-c, --count # Prefix lines by the number of occurrences
-d, --repeated # Only print duplicate lines
-i, --ignore-case # ignore differences in case when comparing
-u, --unique # Only print unique lines

# Examples

cat a b | sort | uniq > c # c is the union of a and b: a | b
cat a b | sort | uniq -b > c # c is the intersection of b: a & b
cat a b b | sort | uniq -u > c # c is the difference of a and b: (a -b)
cat a | sort | uniq -c # create a histogram
```



### curl


#### Reference
- Some of them came from [here](http://www.commandlinefu.com/commands/browse/sort-by-votes)