# File Types in Linux

- Majorly there are six types of files in Linux. To know the type of each file just run `ls -l` which results the all the files and directories present in current directory in long list format. In the output of `ls -l`, we can see some charecters such as `-`, `d`, `l` at left hand side (At start of the permissions) which indicates the type of files in linux. Otherwise we can use the `file` command to simply know the type of the file.

  **Syntax** : `file <filename>`

  **Ex** : `file dev` -> Directory

- Six different types of files in linux are :

  1. **Regular Files** : `-` in the output of `ls -l` indicates the type of the file is regular such as text, data or executable files. 

    **Ex** : `file /etc/hostname` -> /etc/hostname ASCII text

  2. **Link** : `l` in the output of `ls -l` indicates that the type of file is link which means the file links to another file or shortcut which points to actual file. Suppose the file you are acessing regularly is in deep (`/dev/test/prep/commands`), then becomes difficult for us to use absolute path everytime we are acessing that file. So to overcome this we actually create a link to this file by using the following syntax.

     **Syntax** : `ln -s <actual path> <path where you want to store the link>`

     **Ex** : `ln -s /dev/test/prep/commands cmds`

     Here a link gets create between `cmds` and `commands`. To verify this just use `cat cmds` command. If the `cat` command displays the content present in `commands` then a link is created between these two files.

  3. **Directory** : `d` in output of `ls -l` indicated directory.

     **Ex** : `file /tmp` -> directory

  4. **Socket** : `s` indicates the special file that provides the inter-process networking protected by the file's system's access control.

  5. **Special Files** : `c` indicates the mechanism used for input and output, such as files in `/dev`

  6. **Pipe** : `p` indicates a special file that allows processes that communicates each other without using network socket semantics.