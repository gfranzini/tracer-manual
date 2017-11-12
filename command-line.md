# Command line cheat-sheet

### Windows Command Line \(CMD\) vs. Mac OS Terminal

This is a comparison list of common commands to navigate file-systems, including TRACER, using the command line or the terminal. More comprehensive lists can be found on the web.

| **Windows CMD** | TASK | **Mac OS Terminal** |
| :--- | :---: | :--- |
| dir | List files and folders | ls |
| cd | Full path of current folder/directory | pwd |
| cd &lt;path to directory&gt; | Change folder/directory | cd &lt;path to directory&gt; |
| cd.. | One directory up in directory tree | cd .. |
| cd | Move to root directory | cd / |
| mkdir newFolder | Create new directory in current directory | mkdir myFolder |
| echo some-text &gt; fileName\(.txt\) | Create new file | cat &gt; fileName\(.txt\) |
| rmdir myFolder | Remove a directory\* | rmdir myFolder |
| ren oldFolderName newFolderName | Rename a directory | mv oldFolderName newFolderName |
| robocopy myFolder &lt;path to destination directory&gt; | Copy a directory | cp -r myFolder &lt;path to destination directory&gt; |
| move myFolder &lt;path to destination directory&gt; | Move a directory | mv myFolder &lt;path to destination directory&gt; |
| del myFile | Remove a file\* | rm myFile |
| ren oldFileName newFileName | Rename a file | mv oldFileName newFileName |
| copy myFile &lt;path to destination directory&gt; | Copy a file | cp my File &lt;path to destination directory&gt; |
| move myFile &lt;path to destination directory&gt; | Move a file | mv myFile &lt;path to destination directory&gt; |
| cls | Clear the terminal screen | clear |
| type myFile | Concatenate and print a file | cat myFile |
| type C:/../myFile \| find "" /v /c | Count lines a in file | wc -l myFile |

\***IMPORTANT**: Remove/delete command DOES NOT ask for confirmation.

