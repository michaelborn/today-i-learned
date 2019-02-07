# How To Disable Auto-Restart on Docker Containers

So I've had this docker container hanging around my Ubuntu machine since I first developed/started it. It's there whenever I run `docker ps`, and I finally decided I need to stop this useless container from hogging my machine's memory. (After three months!)

```bash
$ docker ps
CONTAINER ID    IMAGE                   ...  CREATED         STATUS          NAMES
2c23e77e395e    dockette/adminer:full   ...  3 months ago    Up 24 hours     boltondocker_adminer_1
```

Turns out [it's pretty easy to disable auto-restart][1] - thanks [Anton Tarasenko][2]!

```bash
docker update --restart=no boltondocker_adminer
```

[1]: https://stackoverflow.com/questions/37599128/docker-how-do-you-disable-auto-restart-on-a-container
[2]: https://stackoverflow.com/users/911945/anton-tarasenko