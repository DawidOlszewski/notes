# regular expressions and grep

`grep` searches for a patterns in provided files - line by line. 
If content of line matches, it will be printed on screen

`grep` modes of operation:
* recursive - looks for current (defaultly) or specified directory and traverse it trecursively
* non-recursive - searches just in specified files or stdin\

`grep`  pattern syntax:
* `-G` - basic regular expression syntax (default)
* `-E` - extended patterns
* `-F` - interprets patterns as fixed string

`grep` common options:
* `grep -e exp1 -e exp2 *.pl` - looks for exp1 or exp2 in every file in *.pl
* `grep -ev exp1 file` - in(v)erts matching
* `grep -R` changes mode to recursive
* `grep -i` Ignore case 
* `grep -c` counts matched lines
* `grep -n` counts matched lines or add line number when found
* `grep -H` adds filename in the prefix `file.txt: sth`
* `grep -w` looks for word
### patterns:
Certain characters, called `metacharacters`, have special meaning and must be escaped (usually with \ if you want to use them as characters). In most syntaxes the metacharacters are:
    `(   )   [   ]  {   }   ^   $   .   \   ?   *   +   |`

| Operator               | Effect                                                                                                    |
| ---------------------- | --------------------------------------------------------------------------------------------------------- |
| .                      | The dot operator matches any single character.                                                            |
| [ ]                    | A box enables a single character to be matched against a character list or character range.               |
| [^ ]                   | A compliment box enables a single character not within a character list or character range to be matched. |
| *                      | An asterisk specifies zero or more characters to match.                                                   |
| ^   (at the beggining) | The caret anchor matches the beginning of the line.                                                       |
| $   (at the end)       | The dollar anchor matches the end of the line.                                                            |



### examples:

| Example           | Match                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------ |
| ".at"             | any three-character string like hat, cat or bat                                            |
| "[hc]at"          | hat and cat                                                                                |
| "[^b]at"          | all the matched strings from the regex ".at" except bat                                    |
| "^[hc]at"         | hat and cat, but only at the beginning of a line                                           |
| "[hc]at$"         | hat and cat, but only at the end of a line                                                 |
| "[A-Z0-9]{10}"    |                                                                                            |
| -iE "[A-Z]{3}"    | contain triple-vowels                                                                      |
| -E "([A-Za-z ]*)" | contain an opening and closing parenthesis, with only letters and single spaces in between |
