# JC 's Lab Report 1 - Remote Access and FileSystem (Week 1)

## `cd` command
* cd with no arguments
```
[user@sahara ~]$ cd
[user@sahara ~]$ 
```
    - working directory: `/home`
    - since there was no argument, and we were already at the root directory, the working directory wasn't changed.
    - No error.
* cd with directory as argument
 ```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
    - working directory: `/home`
    - we were navigated to the directory that was entered as an argument.
    - no error.
* cd with file as argument
 ```
  [user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$ 
```
    - working directory: `/home/lecture1`
    - since a file is not a directory, the terminal returned an error message stating so, and no changes were made to the working directory.
    - error, due to incorrect input type.
      
## `ls` command
* ls with no arguments
  ```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$
```
    - working directory: `/home/lecture1`
    - it listed the files and subdirectories of the current working directory.
    - no error.
* ls with directory as argument
```
  [user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README 
```
    - working directory: `/home`
    - it listed the files and subdirectories of the directory provided as argument.
    - no error.
* ls with file as argument
```
[user@sahara ~]$ ls README
ls: cannot access 'README': No such file or directory
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ ls README
README
```
    - working directory: `/home`, `/home/lecture1`
    - If file is not in the current working directory, an error is returned. If file is in the current working directory, then only that file is displayed.
    - Not an error, because you can use this to check if a particular file is present in the current working directory.

## `cat` command
* cat with no arguments

```
[user@sahara ~/lecture1/messages]$ cat
cd lecture1
cd lecture1
cd
cd
exit
exit
x
x
cd
cd
[user@sahara ~/lecture1/messages]$
```
   - working directory: `/home/lecture1/messages`
   - since there was no input, nothing was printed. however, subsequent entries were printed until cat was exited with `ctrl + d`.
   - I would say it's am error, because I was not expecting such behavior and I don't believe it is a desired outcome.
* cat with directory as argument
```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
[user@sahara ~/lecture1]$
```
   - working directory: `/home/lecture1`
   - it returned an error message due to invalid input.
   - error, because it is designed to read contents of files, not directories.
* cat with file as argument
```
  [user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharse
ts.UTF_8);    
    System.out.println(content);
  }
}```
   - working directory: `/home/lecture1`
   - contents of the file were printed to the screen
   - No error.
