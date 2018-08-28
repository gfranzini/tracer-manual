# Command line: MAC vs. Windows

## Windows Command Line \(CMD\) vs. Mac OS Terminal

This is a comparison list of common commands to navigate file-systems, including TRACER, using the command line or the terminal. More comprehensive lists can be found on the web.

| **Windows CMD** | TASK | **Mac OS Terminal** |
| :--- | :--- | :--- |
| `dir` | List files and folders | `ls` |
| `cd` | Full path of current folder/directory | `pwd` |
| `cd <path to directory>` | Change folder/directory | `cd <path to directory>` |
| `cd..` | One directory up in directory tree | `cd ..` |
| `cd` | Move to root directory | `cd` |
| `mkdir newFolder` | Create new directory in current directory | `mkdir myFolder` |
| `echo some-text > fileName(.txt)` | Create new file | `cat > fileName(.txt)` |
| `rmdir myFolder` | Remove a directory\* | `rmdir myFolder` |
| `ren oldFolderName newFolderName` | Rename a directory | `mv oldFolderName newFolderName` |
| `robocopy myFolder <path to destination directory>` | Copy a directory | `cp -r myFolder <path to destination directory>` |
| `move myFolder <path to destination directory>` | Move a directory | `mv myFolder <path to destination directory>` |
| `del myFile` | Remove a file\* | `rm myFile` |
| `ren oldFileName newFileName` | Rename a file | `mv oldFileName newFileName` |
| `copy myFile <path to destination directory>` | Copy a file | `cp myFile <path to destination directory>` |
| `move myFile <path to destination directory>` | Move a file | `mv myFile <path to destination directory>` |
| `cls` | Clear the terminal screen | `clear` |
| `type myFile` | Concatenate and print a file | `cat myFile` |
| `type C:/../myFile` PIPE\*\* `find "" /v /c` | Count lines in a file | `wc -l myFile` |

\***IMPORTANT**: Remove/delete command DOES NOT ask for confirmation.

\*\*Replace PIPE with the `|` symbol.

