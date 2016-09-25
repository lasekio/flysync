## What it is?

It is simple host-client file synchronizer like rsync. It's purposed to sync files between host and docker-machine 
in dev process.

## Why not just use rsync?

Rsync works well, but it's not meant to quick update changes. After file change detect, rsync is rescanning whole tree 
and compares every file modifed date with client's version. It consumes a lot of time, so changes are delayad even
few seconds after save file. 

This is not acceptable in during dev process.

## How fast flysync is

flysync uses `chokidar` package on host. Depending on file system, cahnge detecting time are different. `flysync` update only
changed files. It doesnt rescan whole tree. Also, it keeps client connection open, so there is no ping effect. 

Most of time delay is not noticable.
