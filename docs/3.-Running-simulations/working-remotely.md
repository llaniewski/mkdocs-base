# Working on a remote host

## Copying files

To copy files you can use the `scp` tool:
```bash
scp user@host:path/file.ext . # copy to host
scp file.ext user@host:path/  # copy from host
```

To copy whole directory, like with `cp` you can use the `-r` option.

Frequently one needs to copy only the files which changed. This can be
achived using `rsunc`:

```bash
rsync -az user@host:path/ .   # copy new files from host
```

This will synchronize the `path/` directory with the current directory.
