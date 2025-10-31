# Filter Commands and Redirections in Linux

## Filter Commands 

- Filter commands are used to filter the files present in Linux File System. These commands are very useful when you want to find some settings in a directory but you don't know in which file those settings are present in that directory. In these scenarios these filter commands will help us to find the files or return something from files (Such as first 10 lines or last 10 lines etc.)


  1. **grep** : `grep` command is used to search a word or given text present in the file. It actually returns the complete line in which given text is located in that file.

     **Syntax** : `grep <text you want to search> <file or file_path>`

     **Ex** : `grep firewall anaconds-kg.cfg` -> firewall --disabled

     Generally grep is case sensitive which means it returns only if it finds the exact match. Suppose if that file contains this word `FIREWALL` then grep won't return it eventhough it is `firewall`. So to make `grep` case-insensitive we actually need to use option `-i`

     **Syntax** : `grep -i firewall anaconda-kg.cfg` -> It will returns all the lines that contains firewall.

     Suppose you want to search for a setting or a word but you doesn't in which file it contains in a directory then actually need to use `*` which indicates all. Suppose you want to find a setting `SELINUX` in `/etc` but you doesn't in which file to search then we can use the following syntax.

     **Syntax** : `grep -r SELINUX /etc/*` 

     Here `-r` is used to search inside the directories which are present in `etc`.

     Suppose if you want to get the lines which doesn't contain the specified word or text then you need to use the option `-v`.

     **Syntax** : `grep -v firewall anaconda-kg.cfg` -> It returns all the lines which doesn't contains firewall.

  2. **less** : `less` command is used to open the file in reader mode but we cannot edit the file as it is opened in read only mode. It opens the file in console itself and we can use up and down arrows to go to next and previous lines. Here we can perform all the operations like copy, search a word etc on the file except edit operations. These operations are same as we have performedin vim editor. To quit the file we just need to press `:q`.

     **Syntax** : `less <filename or filepath>`

  3. **more** : `more` command opens the file percentage format which means it doesn't open all the file. It would open 30% of file at start, later if you hit enter it starts opening remaining percentages. Once you moved to 100% and you want to go to user prompt then just hit down arrow.

     **Syntax** : `more <filename or filepath>`

  4. **head** : `head` command is used to get first 10 lines in the file by default. If you want to get arbitary no of lines then provide the number of lines as an option.

     **Syntax** : `head -n <filename or filepath>` where n is number not symbol. If you want arbitary no of lines then provide the number there.

     **Ex** : `head -20 /etc/hostname` -> It returns first 20 lines of the file hostname. If you won't provide any number then it actually returns first 10 lines.

  5. **tail** " `tail` command returns last 10 lines present in the file. If you want arbitary number of lines from last then provide the number as an option

     **Syntax** : `tail -n <filename or filepath>`

     There is a special option with `tail` command which is `-f` which displays last 10 lines in reader mode. But there is a speciality in this option which is if the file gets changed then those changes are reflected simultaneously if you use the tail with option `-f`.

     **Ex** : `tail -f /var/log/messages`

     Just run this in one window of git bash. Now open another window of git bash and run `vagrant ssh` then you can see changes in messages file.

  6. **cut** : `cut` command is used to retrieve the content from the file if your file looks like but seperated by different delimeters. When your file is well seperated by the delimeters and you want to retrieve the fields of the file then we can use `cut` command.

     **Syntax** : `cut -d<delimeter by which the file is divided> -f<provide the field you want to retrieve> <filepath>`

     **Ex** : `cut -d: -f2 /etc/passwd` -> Here file is sperated by : and iam retriveing the 2nd field.

  7. **awk** : `awk` is also similar to cut command bu we can provide regular expresssions also here.

     **Syntax** : `awk -F'<provide delimeter by which file gets divided>' '{print $<field number>}' <filepath>`

     **Ex** : `awk -F':' '{print $1}' /etc/passwd` -> which gives the first field from the /etc/passwd file.

  8. **sed** : `sed` stands for stream editor, which is used to search a word in the file and replaces with a new word. But we can do this in `vim` editor also. Once you moved to extended command mode just use this syntax to replace a word with new word.
  `%s/<word you actually wanna replace>/<new word>`. This command actually replaces that word with new word only once in each line. If the word repeats multiple times in a single line then it doesn't replace that repeated word. If you want replace a word globally then you need to use an option `g` in the syntax. So the new syntax now is `%s/<word you actually wanna replace>/<new word>/g`. 

     But if you want to replace the same word in multiple files then we need to open each file seperately in vim editor and then run this command multiple times. So to overcome this we can use `sed` command which can able to replace the singlw word with new word in multiple files

     **Syntax** : `sed 's/<word you actually wanna replace>/<new word>/g' <filenames seperated by spaces>`

     **Ex** : `sed 's/coronavirus/covid19/g' *` -> It actually replaces coronavirus with covid19 in all the files present in cureent directory.

     But it actually replace the word with new word and prints it as output but it doesn't edit actual file. To make changes in actual file itself, we need to use an option `-i`.

     **Syntax** : `sed -i 's/<word you actualy wanna replace>/<new word>/g <filenames seperated by spaces>`

  9. **find** : `find` command is used to find the specific files or directory path. It is similar to find option in windows where we actually serach for.

     **Syntax** : `find <some file path where you wanna search> -name <filename>`

     **Ex** : `find /etc -name host*` -> It actually finds the file which starts with hostname in the `etc` directory.

     If you specified `/` then it actually searches for that file in entire system.

     We have some more options with find command. Those are :

     **-name** : Searching file with its name.

     **-inum** : Searching a file with particular inode number.

     **-type** : Searching the file with particular type of the file.

     **-user** : Searching the file by using the owner of the file.

     **-group** : Searching for the files belonging to partiular group.

  10. **locate** : `locate` command is used to search for a file in entire system. Before using the locate command you actually need to update the file database by using `updatedb` command. If you won't update the db then this command would result the file eventhough the file gets deleted but not gets updated in db. (as db won't update automatically).

      **Syntax** : First run `updatedb` and then `locate <filename or filepath>`

      **Ex** : `locate host`  -> it will search for file name that contain word `host`. For this command we doesn't need regular expression like `find` command.

## Output Redirections

- Generally when you executed a command then output is displayed in the console which means the output gets redirected into the console. Suppose if you want to redirect the output to anothor file instead of console then we can use these redirections symbols which redirects the outputs into specified files.

- Redirection is simply cpoying the output of a command and pasting it in a file. We have two redirection symbols in linux. Those are `>` and `>>`.

  **Syntax** : `<command> > <filename>`

  **Ex** : `uptime > temp.txt`

  Here it puts the output of `uptime` in temp.txt. If you want to place the output of another command in sample then this single greater than symbol (`>`) redirection symbol won't do that. It actually overwrites the file and palce the output of new command instead of appending the output to the same file. To append the output in same file, then we need to use `>>` redirection symbol.

  **Ex** : `free -m >> temp.txt`

  In linux we have 3 different types of double greater than symbol redirections. Those are `1>>` , `2>>` and `&>>`. `1>>` is the default one which is equivalent to `>>`. It actually captures the output of the command and appends it into the specified file. But if any error occured while executing the command then it throws the error.

  **2>>** : If you don't want to print the error in the console and you want to redirect into the file then we can use this type of redirection. This redirection append errors occured while executing the command into the specified file. If no errors occured then it actually executes the command and prints the outputin the console.

  **Ex** : `frreee -m 2>> temp.txt`

  **&>>** : This actually captures both outputs and errors and appends them into the specified file. It displays nothing to the console. If command executed successfully then it append the output to the specified file else it appends errors to the specified file.

  Sometimes we neithe rwant to store the output to console nor we want to print them in console. In such cases we actually need to redirect them to `/dev/null` which stored nothing. Generally we use it when we are installing some packages.

  **Ex** `yum install locate -y >> /dev/null` -> This will redirects the output into `/dev/null` file but that files actually holds nothing. If any errors occurs then it will display in the console. Since we need to know if any error occured or not while installation. Because we need to install it properly.

## Piping

- So far we have sending data from one file to another file. What if you want to send data from one program to anothor program. This is what piping does and the operator used to do this is `|` . The Pipe operator sends output from left program as input to the right program.

  Suppose consider a scenario where you  want to retrieve the lines which contain name `centos` in the last 20 lines of the `/var/log/messages` file. In this scenario you need to first find the last 20 lines in the `/var/log/messages` and then you need to pass this a input to find the what are the lines that contain vagrant. To do this i will write command like this.

  **Command** : `tail -20 /var/log/messages | grep -i centos` 

  For scenarios like this we actually use pipe operator. 


