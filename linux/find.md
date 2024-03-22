# find

searches for file depending on they info or metainfo

## common find options:
1. `-name`
2. `-type` (`f` -file,`d` - dir, `l` - symbolic link)
3. `-mtime` - by modification time - withing n days (e.g. `find / -mtime 7`)
4. `-user`/`-group`
5. concatating few options (order matters) with `-not`,`-and`, `-or`\
(e.g. `find /path/to/directory -user john -or -group developers`)
6. `-exec ... {} \;` - examples (sends content fo file to stdin of command)
    * `{} \;` is like this (executing the commands for each found result)
        ```
        ls file1.txt
        ls file2.txt
        ls file3.txt
        ```
    * `{} +`
        ```
        ls file1.txt file2.txt file3.txt
        ```


## examples

### 1. Find a single file by name
`$ find / -name "Foo.txt" 2>/dev/null`

### 2. Find a single file by approximate name
`find / -iname "*foo*txt" 2>/dev/null`

### 3 Find by content -exec
    find ~/Documents/ -name "*txt" -exec grep -Hi penguin {} \; 

    find /path/to/directory -type f -exec chmod 644 {} \; #changes permissions

    find /path/to/directory -name '*.log' -exec mv {} /path/to/destination \; 


### 5. iterate thorugh files with specific extension
    for i in `find . -name "*.java" -type f`; do
        echo "$i"
    done

> [!TIP]
> to avoid problem with unexpected behaviour of exec we can create temporary environmental var
> ``` 
> cmd='cd "$1" && ls -t *.pdf | tail -n2 | sed "s/./\\\\&/g" | xargs rm'
>
> find . -type d -name bak -exec bash -c "$cmd" -- {} \;
> ```

> [!TIP]
> `-exec cmd {} \;` space between `{} \;` is obligatory 

