## Find
The find command will find all the files and directories within the given directory. For example, using `find written_2/' will print all of the files and directories inside the written_2 directory.

```
$ find written_2
written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Abernathy/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch8.txt
written_2/non-fiction/OUP/Abernathy/ch9.txt
written_2/non-fiction/OUP/Berk
...
written_2/travel_guides/berlitz2/Vallarta-History.txt
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
```

Some additional options that we can use for the find command include `-name`, `-delete`, `-maxdepth`, and `-mindepth`.

## -name
The `-name` option will look for files within the directory that has the given name in its file name. It can be used by adding `-name FILE_NAME` after the directory.

Example 1:
```
$ find written_2/ -name ch1.txt
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Fletcher/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch1.txt
written_2/non-fiction/OUP/Rybczynski/ch1.txt
```

In this example, the directory was written_2 and the name given was ch1.txt. The command will then look through written_2 for files named ch1.txt. This can be usedful if there is one specific file that you need to look for as the result will give the path to that file if it exists within the directory.

Example 2:
```
$ find written_2/ -name "*Hawaii*"
written_2/travel_guides/berlitz1/HandRHawaii.txt
written_2/travel_guides/berlitz1/HistoryHawaii.txt
written_2/travel_guides/berlitz1/WhatToHawaii.txt
written_2/travel_guides/berlitz1/WhereToHawaii.txt
```

The `-name` option can also be used with `*`. In this case, the `find` command will look within written_2 for all files containing "Hawaii" in the name. This can be useful when looking for all files with some common naming. The same idea can be used with file types such as with `-name "*.txt"`.

Source: https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/

## -delete
The `-delete` option will delete the files that are found using the `find` command. Using `find` on a directory will find the entire directory, and subsequently delete the entire directory if `delete` is used. Using `find` for just one file will find only that file and delete it if `-delete` is used. When using this option, however, the files will be deleted immediately, so be sure to know what files will be found. A quick run of the find without the `-delete` option beforehand can easily print out the files that would be deleted.

Example 1:

![delete before](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/delete%20before.PNG?raw=true)
```
$ find written_2/non-fiction/OUP/Abernathy/
written_2/non-fiction/OUP/Abernathy/
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Abernathy/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch8.txt
written_2/non-fiction/OUP/Abernathy/ch9.txt
```

Here is the directory before using `-delete` and the files found when using find. These are the files and directories that will be deleted.


```
$ find written_2 -name "*Hawaii*" -delete

```

![delete](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report3/delete%20after.PNG?raw=true)

After the command is run, the Abernathy directory has been deleted as shown. Furthermore, the terminal gives no output after the command is run, immediately deleting Abernathy. This can be useful when you want to delete some files, especially if you are remotely connected to somewhere and cannot manually access the files locally.

Example 2:

```
$ find written_2/ -name "*Hawaii*" -delete

```

`-delete` can also be paired with other options as well. Here, the `find` command will find all files with "Hawaii" in the name and delete them. Again, there is no output after running the `-delete` option.

```
$ find written_2/ -name "*Hawaii*"

```

When `find written_2 -name "*Hawaii*"` is run afterwards, no such files are found since they have been deleted.

Source: https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/

## -maxdepth
`-maxdepth` will use the find command at a maximum depth in directories. A depth of 0 will only find the command-line arguments (the given directory) and a depth of 1 will refer to the given directory. If a maxdepth of 2 is used, then `find` will only search within the given directory and the next level of subdirectories.

Example 1:
```
$ find written_2 -maxdepth 2
written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```

The `find` only found files and directories into one level of subdirectories since a maxdepth of 2 (`written_2/*`) was used. Once it reaches depth 3, which would be in `written_2/non-fiction/OUP`, `written_2/travel_guides/berlitz1`, and `written_2/travel_guides/berlitz2`, it stops searching. This can be useful if you only need to find files within a certain depth and do not want to search every single subdirectory. Otherwise, the output may become clogged with unncessary files.

Example 2:
```
$ find written_2 -maxdepth 3 -name "*.txt"
written_2/travel_guides/berlitz1/HandRHongKong.txt
written_2/travel_guides/berlitz1/HandRIbiza.txt
written_2/travel_guides/berlitz1/HandRIsrael.txt
written_2/travel_guides/berlitz1/HandRIstanbul.txt
written_2/travel_guides/berlitz1/HandRJamaica.txt
written_2/travel_guides/berlitz1/HandRJerusalem.txt
written_2/travel_guides/berlitz1/HandRLakeDistrict.txt
written_2/travel_guides/berlitz1/HandRLasVegas.txt
written_2/travel_guides/berlitz1/HandRLisbon.txt
written_2/travel_guides/berlitz1/HandRLosAngeles.txt
written_2/travel_guides/berlitz1/HandRMadeira.txt
written_2/travel_guides/berlitz1/HandRMadrid.txt
...
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt
written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt
written_2/travel_guides/berlitz2/Vallarta-History.txt
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
```

Similarly to `-delete`, `-maxdepth` can also be used in tandem with other options. This will search for all .txt files within a depth of 3 (`written_2/travel_guides/berlitz2/` or `written_2/travel_guides/berlitz1/`). None of the .txt files within the `non-fiction` subdirectory will be found since they have a depth of 4 (`written_2/non-fiction/OUP/*`). This can be useful when searching for some specific files, but only within a certain depth as to not fill the terminal.

Source: https://linux.die.net/man/1/find

## -mindepth
Similar to `-maxdepth`, `-mindepth` will search for items within a minumum depth. Depth will also be the same, where 0 refers to the command-line arguments, 1 to the given directory, and 2 and beyond as its subdirectories.

Example 1:
```
$ find written_2 -mindepth 2
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
...
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt
written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt
written_2/travel_guides/berlitz2/Vallarta-History.txt
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
```

The output is similar to `find written_2`, but since a depth of 2 is used, `written_2/non-fiction`, `written_2/travel_guides` and any content directly in `written_2/` are not found as it normally would in `find written_2`. This command is useful just like `-maxdepth` to not look for everything, which may clutter the terminal.

Example 2:
```
$ find written_2 -mindepth 4 -name "*.txt"
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
...
written_2/non-fiction/OUP/Kauffman/ch8.txt
written_2/non-fiction/OUP/Kauffman/ch9.txt
written_2/non-fiction/OUP/Rybczynski/ch1.txt
written_2/non-fiction/OUP/Rybczynski/ch2.txt
written_2/non-fiction/OUP/Rybczynski/ch3.txt
```
`-mindepth` can also be paired with other options as well. `find written_2 -mindepth 4 -name "*.txt"` will find all .txt files within a depth of 4 (`written_2/non-fiction/OUP/*`). All the .txt files in `written_2/travel_guides` are at a depth of 3 (`written_2/travel_guides/*`), so they are not found and printed out. Again, this is useful in narrowing the search for `find` in order to not completely fill the terminal with every file and directory.

Source: https://linux.die.net/man/1/find
