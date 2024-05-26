# fuser - find user

if sth has set cwd on some file it cannot be deleted`

prints process and users that use some file\
option: -ki

```bash
fuser -v $(which bash) 
fuser -n tcp /
```

