# Run PgHero with Docker Compose

## Setup
### Install Dependencies
- [Docker CE](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Configure YAML Files for Your Environment
You will want to set up the two `.yml` files in this repository to match the Postgres environment that you are wanting to run PgHero against. The bare minimum steps are as follows.
- in `docker-compose.yml`
  - set the username, password, and hostaddress values in `DATABASE_URL`.
  - under the `volumes` key, set the first path to match the location of your `pghero.yml` file on your computer.
- in `pghero.yml`
  - set up keys like those in the example file to correspond with the databases you would like to access with PgHero, replacing `database1` and `database2` with the actual names of the databases.
  - change the value of the `url` key to correspond the username, password, host server address, and database name that you would like to connect to.
  - **Note**: PgHero _seems_ to support as many of these database entries as you would like, pointed at multiple hosts. I have tested and confirmed it working with 30 databases, with 3 separate hosts and 10 databases on each host.


## How to Use
Run the following command from within the directory containing your `docker-compose.yml` and `pghero.yml` files.
````bash
docker-compose up
````
Once the container has fully spun up, visit port `localhost:8080` in your web browser to access PgHero. When accessing it, you will see output from the PgHero container in the terminal from which the container was launched.  
To shut down the container, use `Ctrl+C` in the terminal that is running the container.

### Source Repos
- [Docker CE](https://github.com/docker/docker-ce)
- [Docker Compose](https://github.com/docker/compose)
- [PgHero](https://github.com/ankane/pghero)
