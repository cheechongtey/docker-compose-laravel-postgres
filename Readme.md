# docker-compose-laravel-postgres
A pretty simplified Docker Compose workflow that sets up a LEMP network of containers for local Laravel development. You can view this [repo](https://github.com/aschmelyun/docker-compose-laravel) for more details.
## Usage

To get started, make sure you have [Docker installed](https://docs.docker.com/docker-for-mac/install/) on your system, and then clone this repository.

Next, run `cp .env.example .env` to create a new .env file. Then, update the `.env` file with your postgres database information.

Next, navigate in your terminal to the directory you cloned this, and spin up the containers for the web server by running `docker-compose up -d --build app`.

After that completes, create a folder name src then clone ur repo in this folder

**Note**: Your POSTGRES database host name should be `laravel-db`, **not** `localhost`. The username and database should both be following the variable u setup in .env. 

Bringing up the Docker Compose network with `app` instead of just using `up`, ensures that only our site's containers are brought up at the start, instead of all of the command containers as well. The following are built for our web server, with their exposed ports detailed:

- **nginx** - `:80`
- **postgres** - `:5432`
- **php** - `:9000`

Three additional containers are included that handle Composer, NPM, and Artisan commands *without* having to have these platforms installed on your local computer. Use the following command examples from your project root, modifying them to fit your particular use case.

- `docker-compose run --rm composer update`
- `docker-compose run --rm npm run dev`
- `docker-compose run --rm artisan migrate`