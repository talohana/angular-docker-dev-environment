# Angular Docker Dev Environment

Develop an Angular app entirely on docker

## Prerequisites

- [Docker](https://docs.docker.com/) environment and [docker-compose](https://docs.docker.com/compose/) binaries installed.

- Basic knowledge and understanding of [Docker](https://docs.docker.com/), [Angular CLI](https://cli.angular.io/) and [npm](https://www.npmjs.com/)

# Notes

- For [git-bash](https://git-scm.com/downloads) users, prefix the interactive docker command with `winpty`

# Installing

Create Angular project by running

```
docker-compose -f docker-compose.seed.yml run seed
```

After successful initialization remove the `docker-compose.seed.yml` file

# Running

Start the development server run `docker-compose up -d --build`

Inspect the server logs with `docker logs -f dev`

Access the dev server from your browser run `docker-machine ip` and access the given ip at port 4200.  
Once the server is running it will poll changes from host and auto reload the page.

Attach the container with

```
docker exec -it dev sh
```

## Authors

- **Tal Ohana**

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
