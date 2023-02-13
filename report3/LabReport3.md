## Find
The find command will find all the files and directories within the given directory. For example, using `find written_2/' will print all of the files and directories inside the written_2 directory.

![find example](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/find.PNG?raw=true)

Some additional options that we can use for the find command include `-name`, `-delete`, `-maxdepth`, and `-mindepth`.

## -Name
The `-name` option will look for files within the directory that has the given name in its file name. It can be used by adding `-name name` after the directory.

Example 1:

![-name ex1](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/-name%20example.PNG?raw=true)

In this example, the directory was written_2 and the name given was ch1.txt. The command will then look through written_2 for files named ch1.txt. This can be usedful if there is one specific file that you need to look for as the result will give the path to that file if it exists within the directory.

Example 2:

![name ex2](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/name%20example2.PNG?raw=true)

The `-name` option can also be used with ``*`. In this case, the `find` command will look within written_2 for all files containing "Hawaii" in the name. This can be useful when looking for all files with some common naming. The same idea can be used with file types such as with `-name "*.txt"`.
