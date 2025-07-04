# Vim Editor

## Introduction

- Generally Vim Editor is used to edit the files present in the Linux. In Ubuntu distros, `vim` editor is installed by default. But in centos distros it is not installed by default. So to install `vim editor` in linux, we actually need to use the following syntax.

  **Syntax** : `sudo yum install vim`

- To open a file in `vim` editor, we actually need to use the following syntax.

  **Syntax** : `vim <filename or filepath>`

  **Ex** : `vim testfile1.txt`

  If the file provided doesn't exist in current directory or at specified path then linux automatically creates the file and opens it in vim editor.

## Modes in Vim Editor

- There are actually three modes in vim editor. Those are :

  1. Command Mode

  2. Insert Mode

  3. Extended Command Mode

- When you run the `vim <filename>`, then vim editor opens in command mode by default. When we are in command mode we cannot perform anything on that file which means editing the file, etc. If you want to edit the file like inserting some content or removing some content, you actually need to move to insert mode. To switch to insert mode we actually need to press `i` on the keyboard. When you press `i` on the keyboard then you see `--insert--` at the bottom of the file which means you are in insert mode. You you can perform whatever you want on that file. Once you performed the modifications on that file, the press `esc` button to return back to command mode. Now to move to extended command mode you actually need to press colon `:` , then you can see colon at the bottom of the file. Generally extended command mode is used to save and quit (or exit) the file.


- We have some operations which we can perform, when we are in extended command mode. Those are :

  1. **Esc + :w** : This is used to save the changes.

  2. **Esc + :q** : Used to quit the file.

  3. **Esc + :wq** : Used to save and quit the file.

  4. **Esc + :wq!** : Save and quit the file forcefully.

  5. **Esc + :w!** : Save the file forcefully.

  6. **Esc + :q!** : Quit the file forcefully.

  7. **Esc + :se nu** : Set the line numbers in the file.

  8. **Esc + :se nonu** : To remove the set line numbers in the file.

  9. **Esc + x** : To save and quit the file.

  10. **Esc + x!** : To save and quit from the file forcefullly.

## Some more Operations in Vim Editor

- We can perform these operations when we are in command mode itself.

  1. **gg** : To go to the begining of the file.

  2. **G** : To go the end of the file.

  3. **w** : TO move the cursor forward word by word.

  4. **b** : To move cursor backward word by word.

  5. **nw** : To move cursor forward to n words. If you click `2 + w` then we move 2 words forward.

  6. **nb** : To move cursor backword by n words.

  7. **u** : To undo the previous changes (It will do word level only).

  8. **U** : To undo the previous changes (It will do entire line).

  9. **yy** : To copy a line where cursor is pointed out.

  10. **nyy** : To copy n lines from the current line.  Ex : `4yy` which copies 4 lines from the current line where cursor is pointed now. 

  11. **p** : To paste the line below the cursor

  12. **P** : To paste line above the cursor.

  13. **dd** :  To delete the entire line. It actually cuts the line where cursor is pointed out, so that you can paste wherever you want it.If you want to delete that line then just don’t paste it once you deleted.

  14. **d** : To delete n no of line from cursor position.

  15 **/** : Search a word in af file.

