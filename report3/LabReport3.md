## Find
The find command will find all the files and directories within the given directory. For example, using `find written_2/' will print all of the files and directories inside the written_2 directory.

![find example](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/find.PNG?raw=true)

Some additional options that we can use for the find command include `-name`, `-delete`, `-maxdepth`, and `-mindepth`.

## -Name
The `-name` option will look for files within the directory that has the given name in its file name. It can be used by adding `-name name` after the directory.

Example 1:
```
$ find written_2/ -name ch1.txt
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Fletcher/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch1.txt
written_2/non-fiction/OUP/Rybczynski/ch1.txt
```
![-name ex1](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/-name%20example.PNG?raw=true)

In this example, the directory was written_2 and the name given was ch1.txt. The command will then look through written_2 for files named ch1.txt. This can be usedful if there is one specific file that you need to look for as the result will give the path to that file if it exists within the directory.

Example 2:
```
$ find writte_2/ -name "*Hawaii*"
written_2/travel_guides/berlitz1/HandRHawaii.txt
written_2/travel_guides/berlitz1/HistoryHawaii.txt
written_2/travel_guides/berlitz1/WhatToHawaii.txt
written_2/travel_guides/berlitz1/WhereToHawaii.txt
```

![name ex2](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/name%20example2.PNG?raw=true)

The `-name` option can also be used with `*`. In this case, the `find` command will look within written_2 for all files containing "Hawaii" in the name. This can be useful when looking for all files with some common naming. The same idea can be used with file types such as with `-name "*.txt"`.

Source: https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/

## -Delete
The `-delete` option will delete the files that are found using the `find` command. Using `find` on a directory will find the entire directory, and subsequently delete the entire directory if `delete` is used. Using `find` for just one file will find only that file and delete it if `-delete` is used. When using this option, however, the files will be deleted immediately, so be sure to know what files will be found. A quick run of the find without the `-delete` option beforehand can easily print out the files that would be deleted.

Example 1:

![delete before](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/delete%20before.PNG?raw=true)
![files deleted](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/files%20deleted.PNG?raw=true)

Here is the directory before using `-delete` and the files found when using find. These are the files and directories that will be deleted.


![delete](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/delete.PNG?raw=true)

![delete](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/delete%20after.PNG?raw=true)

After the command is run, the Abernathy directory has been deleted as shown. Furthermore, the terminal gives no output after the command is run, immediately deleting Abernathy. This can be useful when you want to delete some files, especially if you are remotely connected to somewhere and cannot manually access the files locally.

Example 2:

![delete paired](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/delete%20paired.PNG?raw=true)

`-delete` can also be paired with other options as well. Here, the `find` command will find all files with "Hawaii" in the name and delete them.

![delete paired after](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/delete%20paired%20after.PNG?raw=true)

When `find written_2 -name "*Hawaii*"` is run afterwards, there is no output as those files are deleted.
