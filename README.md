## Now apply template to container
```sh
bastille bootstrap https://github.com/bastille-templates/opensearch
bastille template opensearch bastille-templates/opensearch
```
Edii file /usr/local/bastille/jails/container/fstab
```sh
fdesc	/dev/fd		fdescfs		rw	0	0
proc	/proc		procfs		rw	0	0
```

## License
This project is licensed under the BSD-3-Clause license.