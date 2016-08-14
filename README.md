# Template to run own letsencrypt private docker registry on the letsencrypt domain

to start service use ```docker-compose up```

Original readme:

# docker-letsencrypt-nginx-proxy-companion-examples

This repository is meant to be a starting point for working with [nginx-proxy](https://github.com/jwilder/nginx-proxy), [docker-gen](https://github.com/jwilder/docker-gen) and [docker-letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion) by providing basic working bootstrapped examples that combines them.

## Choosing how to run things

Running docker containers can be done either using the [command line interface](https://docs.docker.com/engine/reference/commandline/cli/) (CLI), or using [docker-compose](https://docs.docker.com/compose/overview/)

## docker run

Replace all the default "site.example.com" and "mail@example.com" occurrences in docker-run/simple-site/docker-run.sh for your publicly accessible domain redirecting to the server running the script.

```
$ ./docker-run.sh
```

## docker-compose v1

While docker-compose v1 file version [isn't advised for starting new project](https://docs.docker.com/compose/compose-file/#upgrading), docker-gen hasn't yet officially resolved [the issue](https://github.com/jwilder/nginx-proxy/issues/304) raised by new networking in docker-compose v2, you might find it easier to stick with v1.

Replace all the default "site.example.com" and "mail@example.com" occurrences in docker-compose/v1/simple-site/docker-compose.yml for your publicly accessible domain redirecting to the server running the script.

```
$ docker-compose up
```

## docker-compose v2

V2 support for docker-gen is being done through @almereyda's [unofficial solution](https://github.com/jwilder/nginx-proxy/issues/304#issuecomment-189775983). See above for compose v1.

Replace all the default "site.example.com" and "mail@example.com" occurrences in docker-compose/v2/simple-site/docker-compose.yml for your publicly accessible domain redirecting to the server running the script.

First, you'll need to create an external docker network named 'nginx-proxy' (or change the name in compose file).

```
docker network create -d bridge nginx-proxy
```

You'll only need to do this once.

```
$ docker-compose up
```

## Debugging

You should use [docker logs](https://docs.docker.com/engine/reference/commandline/logs/) to see the output of your daemonized containers.

```
$ docker logs nginx
```

You can also checkout the docker-gen generated "default.conf" file using [docker exec](https://docs.docker.com/engine/reference/commandline/exec/)

```
$ docker exec -it nginx-gen cat /etc/nginx/conf.d/default.conf
```

# Notes

If you want to help out the community, feel free to submit a PR with other examples for popular site/apps such as Wordpress, ghost...

I'll try to add some myself provided this repo gets enough stars.
