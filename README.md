# Angular Docker Dev Environment

Develop an Angular app entirely on docker

For a more detailed explanation check out [my blogpost](https://talohana.com/blog/dockerizing-angular-environment)

## Prerequisites

- [Docker](https://docs.docker.com/) environment and [docker-compose](https://docs.docker.com/compose/) binaries installed.

- Basic knowledge and understanding of [Docker](https://docs.docker.com/), [Angular CLI](https://cli.angular.io/) and [npm](https://www.npmjs.com/)

# Notes

- For [git-bash](https://git-scm.com/downloads) users, prefix the interactive docker command with `winpty`
- Before installing, you can override the `ng new` command at the `docker-compose.seed.yml` entrypoint property

# Installing

Create Angular project by running

```
docker-compose -f docker-compose.seed.yml run seed
```

After successful initialization remove the `docker-compose.seed.yml` file

# Running

Start the development server run `docker-compose up -d --build`

Inspect the server logs with `docker-compose logs -f dev`

Access the dev server from your browser run `docker-machine ip` and access the given ip at port 4200.  
Once the server is running it will poll changes from host and auto reload the page.

Attach the container with

```
docker-compose exec dev sh
```

## Copying node_modules

You should copy the `node_modules` directory from your container after every package addition, to do so run:

```
docker cp dev:/usr/src/app/package-lock.json . && \
docker cp dev:/usr/src/app/node_modules - > temp_node_modules.tar && \
    tar -xf temp_node_modules.tar && \
    rm -f temp_node_modules.tar
```

This process might take some time, but keep in mind you won't run it so often

## Authors

- **Tal Ohana**

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
