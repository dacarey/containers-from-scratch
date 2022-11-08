# containers-from-scratch
Writing a container in a few lines of Go code, as seen at [DockerCon 2017](https://www.youtube.com/watch?v=MHv6cWjvQjM&t=1316s) and on [O'Reilly Safari](https://www.safaribooksonline.com/library/view/how-to-containerize/9781491982310/)

## Dave's additional notes

h1.    How I run this on Linux
```
sudo env "PATH=$PATH" go run main.go run /bin/bash
```
This is to avoid a common error [*fork/exec /proc/self/exe: operation not permitted*](https://stackoverflow.com/questions/72543182/fork-exec-proc-self-exe-operation-not-permitted)

h1.    How I build the container Filesystem
```
rsync -aAXv / --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/home/*","/opt/*","/snap/*","/usr/local/*","/usr/src/*","/var/*","/vagrant/*"} /vagrant/rootfs
```
Kudos to this [StackExchange thread and answere](https://askubuntu.com/questions/1049930/how-to-copy-root-file-system-in-ubuntu#answer-1231934)

