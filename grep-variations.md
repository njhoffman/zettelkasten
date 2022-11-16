## Differences between grep, pgrep, egrep, and fgrep (Linux):

### grep

grep is an acronym that stands for "Global Regular Expressions Print". grep is a program which scans a specified file or files line by line, returning lines that contain a pattern.
A pattern is an expression that specifies a set of strings by interpreting characters as meta-characters.
For example the asterisk meta character (`*`) is interpreted as meaning "zero or more of the preceding element".
This enables users to type a short series of characters and meta characters into a grep command to have the computer show us what lines in which files match.
The standard grep command looks like:

```bash
  grep <flags> '<regular expression>' <filename>
  grep prints the search results to the screen (stdout) and returns the following exit values:
#  1   A match was found.
#  2   No match was found.
# >2   A syntax error was found or a file was inaccessible (even if matches were found).
```

Some common flags are:
  -c for counting the number of successful matches and not printing the actual matches,
  -i to make the search case insensitive,
  -n to print the line number before each match printout,
  -v to take the complement of the regular expression (i.e. return the lines which don't match),
  -l to print the file names of files with lines which match the expression.

### egrep

egrep is an acronym that stands for "Extended Global Regular Expressions Print".

The 'E' in egrep means treat the pattern as a regular expression. "Extended Regular Expressions" abbreviated 'ERE' is enabled in egrep.
egrep (which is the same as grep -E) treats +, ?, |, (, and ) as meta-characters.

In basic regular expressions (with grep), the meta-characters ?, +, {, |, (, and ) lose their special meaning.
If you want grep to treat these characters as meta-characters, escape them \?, \+, \{, \|, \(, and \).

For example, here grep uses basic regular expressions where the plus is treated literally, any line with a plus in it is returned.

```bash
grep "+" myfile.txt
egrep on the other hand treats the "+" as a meta character and returns every line because plus is interpreted as "one or more times".
egrep "+" myfile.txt
```

Here every line is returned because the + was treated by egrep as a meta character. normal grep would have searched only for lines with a literal +.

### fgrep
fgrep is an acronym that stands for "Fixed-string Global Regular Expressions Print".

fgrep (which is the same as grep -F) is fixed or fast grep and behaves as grep but does NOT recognize any regular expression meta-characters as being special. The search will complete faster because it only processes a simple string rather than a complex pattern.

For example, if I wanted to search my .bash_profile for a literal dot (.) then using grep would be difficult because I would have to escape the dot because dot is a meta character that means 'wild-card, any single character':

```bash
grep "." myfile.txt
# The above command returns every line of myfile.txt. Do this instead:
fgrep "." myfile.txt
```

Then only the lines that have a literal '.' in them are returned. fgrep helps us not bother escaping our meta characters.

### pgrep
pgrep is an acronym that stands for "Process-ID Global Regular Expressions Print".
pgrep looks through the currently running processes and lists the process IDs which matches the selection criteria to stdout.
pgrep is handy when all you want to know is the process id integer of a process.
For example, if I wanted to know only the process ID of my mysql process I would use the command pgrep mysql which would return a process ID like 7312.
