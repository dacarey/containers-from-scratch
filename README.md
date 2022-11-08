# Containers from Scratch
Writing a container in a few lines of Go code, as seen at [DockerCon 2016](https://www.youtube.com/watch?v=MHv6cWjvQjM&t=1316s) and on [O'Reilly Safari](https://www.safaribooksonline.com/library/view/how-to-containerize/9781491982310/)

This is forked from Liz Rice's original repository,  purely to allow me to add some extra setup notes

Massive kudos to Liz for this. It really showcases how the underlying concepts of cgroups,  namespaces,  chrooted file systems ( a.k.a images) can be put together to form the bigger concept of a 'container'


##   How I run this on Linux
```
sudo env "PATH=$PATH" go run main.go run /bin/bash
```
This is to avoid a common error [*fork/exec /proc/self/exe: operation not permitted*](https://stackoverflow.com/questions/72543182/fork-exec-proc-self-exe-operation-not-permitted)

##   How I build the container Filesystem
```
rsync -aAXv / --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/home/*","/opt/*","/snap/*","/usr/local/*","/usr/src/*","/var/*","/vagrant/*"} /vagrant/rootfs
```
Kudos to this [StackExchange thread and answere](https://askubuntu.com/questions/1049930/how-to-copy-root-file-system-in-ubuntu#answer-1231934)

Remember to then also create the mytemp directory. It is helpful to create a directory CONTAINER_FILESYSTEM ( yes in uppercase) so it is obvious that you are in that directory when you start the container.
