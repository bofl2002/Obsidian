
[[Virtualisering]]



**

# Linux commands

Bash - Bourne Again Shell

Inden i en terminal har du det, der kaldes en shell. Dette er en del af operativsystemet, der definerer, hvordan terminalen vil opføre sig og tager sig af at køre (eller udføre) kommandoer for dig. Der findes forskellige shells tilgængelige, men den mest almindelige kaldes BASH, som står for Bourne Again SHell. Denne vejledning antager, at du bruger BASH som din shell.

Shortcuts:

- echo: viser en systemvariabel, der angiver din historik størrelse
    

- echo $HISTSIZE
    

- pwd: Print Working Directory - viser det directory du arbejder i.
    
- ls: List
    
- cd: change directory
    

Path:

- ~ (tilde) - Dette er en genvej til din hjemmemappe. /home/ryan/Documents eller ~/Documents
    
- . (punktum) - Dette er en reference til din nuværende mappe. Det kunne også skrives som ./Documents 
    
- .. (dobbelt punktum) - Dette er en reference til den overordnede mappe. Du kan bruge dette flere gange i en sti for at blive ved med at gå op i hierarkiet. kommandoen ls ../../ og dette ville lave en liste over rodmappen.
    

file: obtain information about what type of file a file or directory is.

ls -a: List the contents of a directory, including hidden files.

man <command>: Look up the manual page for a particular command.

man -k <search term>: Do a keyword search for all manual pages containing the given search term.

/<term>: Within a manual page, perform a search for 'term'

n: After performing a search within a manual page, select the next found item.

mkdir : Make Directory -p: make parent directories as needed -v: mkdir tell us what it is doing

rmdir : remove directory. -r:  sletter directory og filerne

touch: create blank files touch [options] <filename>

cp: copy files - cp [options] <source> <destination> :  -r:  Recursive : copy directories

mv: Flyt fil eller directory - mv [options] <source> <destination>

mv: rename fil - mv <filnavn>  <nyt filnavn>

vi: (insert = i or Edit)  esc 

ZZ (Note: capitals) - Save and exit  
:q! - discard all changes, since the last save, and exit  
:w - save file but don't exit  
:wq - again, save and exit

cat: cat<file>  
less: less<file> brug piletaster til at veksle mellem siderne  
esc: tilbage til edit mode

:set nu: enable linenumbers i edit

- Arrow keys - move the cursor around
    
- j, k, h, l - move the cursor down, up, left and right (similar to the arrow keys)
    
- ^ (caret) - move cursor to beginning of current line
    
- $ - move cursor to end of the current line
    
- nG - move to the nth line (eg 5G moves to 5th line)
    
- G - move to the last line
    
- w - move to the beginning of the next word
    
- nw - move forward n word (eg 2w moves two words forwards)
    
- b - move to the beginning of the previous word
    
- nb - move back n word
    
- { - move backward one paragraph
    
- } - move forward one paragraph
    

Deleting content  
x - delete a single character  
nx - delete n characters (eg 5x deletes five characters)  
dd - delete the current line  
dn - d followed by a movement command. Delete to where the movement command would have taken you.       eg d5w means delete 5 words)

u - Undo the last action (you may keep pressing u to keep undoing)  
U (Note: capital) - Undo all changes to the current line

Permissions

- r read - you may view the contents of the file.
    
- w write - you may change the contents of the file.
    
- x execute - you may execute or run the file if it is a program or script.
    
- chmod 755 <script>. - tjekker om script kan køres
    
- chmod (change mode) is a command used to change the access permissions of files and directories
    

And three categories of users:

- u (user/owner)
    
- g (group)
    
- o (others)
    
- a (all)
    

  

Filters

head [-number of lines to print] [path]  
tail [-number of lines to print] [path]  
sort [-options] [path]  
nl [-options] [path]  
wc(word count) [-options] [path] -l (antal linjer) -w (antal ord) -m (antal karaterer)  
cut [-options] [path]  
sed (Stream Editor): <expression> [path] s/search/replace/g

uniq [options] [path] - removes duplicates  
tac [path] data it will print the last line first

Grep

egrep [command line options] <pattern> [path] - ex. egrep -n 'mellon' mysampledata.txt -c (antal linjer med ‘Mellon’

Regular expressions

- . (dot) - a single character.
    
- ? - the preceding character matches 0 or 1 times only.
    
- * - the preceding character matches 0 or more times.
    
- + - the preceding character matches 1 or more times.
    
- {n} - the preceding character matches exactly n times.
    
- {n,m} - the preceding character matches at least n times and not more than m times.
    
- [agd] - the character is one of those included within the square brackets.
    
- [^agd] - the character is not one of those included within the square brackets.
    
- [c-f] - the dash within the square brackets operates as a range. In this case it means either the letters c, d, e or f.
    
- () - allows us to group several characters to behave as one.
    
- | (pipe symbol) - the logical OR operation.
    
- ^ - matches the beginning of the line.
    
- $ - matches the end of the line.
    

## Piping and Redirection  
Redireting to file:  
> save output to file:  > filenavn  
>> append out to existing file  
Redireting from file:  
< read data from file

Piping

|  - ls | head -3 (viser kun 3 flíler i output) - ls | head -3 | tail -1 (viser kun sidste fil i output af de tre filer)

Wildcards

- * - represents zero or more characters
    
- ? - represents a single character
    
- [] - represents a range of characters
    

Process Management

Top: Snapshot of what is currently happening on the system  
ps [aux]: show a complete system view  
ps aux | grep 'firefox' - find PID  
kill [signal] <PID>: kill a process - kill -(1-9 ) 6978 - 1 er standard, 9 er sledge hammer  
Jobs: Lists currently running background jobs  
Sleep: sleep does is wait a given number of seconds and then quit

Scripting  
echo <message>  
which <program>  
#! - Shebang. Indicates which interpreter a script should be run with.  
echo - Print a message to the screen.  
which - Tells you the path to a particular program.  
$ - Placed before a variable name when we are referring to it's value.  
` ` - Backticks. Used to save the output of a program into a variable.  
date - Prints the date.  
if [ ] then else fi - Perform basic conditional logic.

  

  


**