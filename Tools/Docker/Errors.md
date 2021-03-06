# Docker errors

## docker-compose exited with code 0

### [Container stops immediately with docker-compose but runs fine with Docker (github.com/docker)](https://github.com/docker/compose/issues/5016)

 `tty: true`

### [Doesn't have anything to run](https://github.com/docker/compose/issues/4148)

But to answer the original question, the reason datastore exits with code 0 is because you don't define a command to be run. It's not an error, just means the container doesn't have anything to run and terminates as result.

It's fine, the container has no running script but it is set up. Check with docker ps`. 
Should be defined in the command. See [Keep-container-alive](Keep-container-alive.md)


## npm ERR! enoent ENOENT: no such file or directory, open '/package.json'

package.json is in the directory. 

### Possible cause

To work with a file in the Dockerfile.

* Working directory needs to be set.
* package.json file needs to be copied.

```dockerfile
WORKDIR /var/www
COPY package.json /var/www
```

## ERROR Error: Cannot find module 'dotenv'

* [The node_modules Volume Trick (jdlm.info)](http://jdlm.info/articles/2016/03/06/lessons-building-node-app-docker.html#the-node_modules-volume-trick)

Add to `docker-compose.yml` volumes

```yaml
services:
  my-container:
    volumes:
    - /var/www/node_modules
```

## Container already in use

Check all containers (even exited).

```shell
docker ps -a
```

Go to the according container-compose directory and exec

```shell
docker-compose down --remove-orphans
```