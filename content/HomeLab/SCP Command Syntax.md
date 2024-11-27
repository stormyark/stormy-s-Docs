---
tags:
  - HomeLab
  - linux
  - shell
---


```scheme
scp [OPTION] [user]@[SRC_HOST]:file1 [user]@[DEST_HOST]:file2
```

`[USER]`: username
`[SRC_HOST]`: ip
`[OPTION]`:

- `P` - Specifies the remote host ssh port.
- `p` - Preserves file modification and access times.
- `q` - Use this option if you want to suppress the progress meter and non-error messages.
- `C` - This option forces `scp` to compress the data as it is sent to the destination machine.
- `r` - This option tells `scp` to copy directories recursively.