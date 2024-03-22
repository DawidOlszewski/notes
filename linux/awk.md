# awk

`ps | awk '{print $0}` - prints all

`ps | awk '{print $1}` - prints first line

`awk -F ":" ` - change the field separator top ':'

`awk -F ":" '{print $1}' /etc/passwd`

`awk -F ":" 'pattern-regex {print $NF}' /etc/passwd`

`$NF` is the last field in a line

`awk -F "/" '/^\// {print $NF}' /etc/shells | sort | uniq`

`awk 'length($0) > 7' /etc/shells` 

`ps ef | awk '{if ($NF == "/bin/bash") print $0}`





