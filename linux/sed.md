# sed - stream editor

by default sed prints changes text to stdout 

### substitution

`sed 's/find/repolace/' input.txt` looks for the first instance of find in a line and replaces it

`sed 's/find/repolace/g' input.txt` looks for every instance of find in a line and replace

`-i` "**I**n-place" - writes changes to current file

`sed '/lineregex/s/the/THE`

### deleteion

`sed '/lineregex/d` **d**deletes lines that matches the pattern

### printing
`sed '/lin-reg/p`

### multiple sed
`sed -e pattern1 -e pattern2`

> [!NOTE]
> instead of using `/` as a separtor, yoiu can use `#`

### examples:
`sed -i 's/ *$//' file-with-spaces`

`sed -i '/^$/d' file-with-empty-lines`

`sed -i 's/[a-z]/\U&/g' lower-case` - `\U&` makes it uppercase

