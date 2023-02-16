---
description: >-
  Feeling adventurous? Here are the description and explanation of the
  underlying tools that are used to make the project run.
---

# Long Start

### The technical stack <a href="#the-stack" id="the-stack"></a>

Progressively is one product that needs multiple tools to run on different platforms. Here is a list of what is needed to make it run from the user interface until finally reaches the databases.

* **frontend (dashboard)**: built with [Remix.run](https://remix.run/)
* **backend (API/Websockets)** built with [Nestjs](https://nestjs.com/)
* **database access/migrations** built with [Prisma](https://www.prisma.io/)
* **databases**: [Postgres](https://www.postgresql.org/) and [Redis](https://redis.io/) (for WebSocket backend)

All of the packages are written in [TypeScript](https://www.typescriptlang.org/).

### The repository

The project code is stored in [a repository on the GitHub platform](https://github.com/progressively-crew/progressively). It's built using a "mono-repo" approach meaning that one repository can host multiple different packages. In our case, Progressively is using [Lerna](https://lerna.js.org/) to help manage the dependencies between [these packages](https://github.com/progressively-crew/progressively/tree/master/packages).

### What has to be done to start the project?

1. Get the project locally
2. Create `.env` files for the `frontend` and `backend` packages
3. Start Postgres
4. Start Redis
5. Setup the monorepo
6. Create Postgres tables
7. Start the frontend & backend project
8. Follow the onboarding steps

### Let's get into it, step by step

#### Get the project locally

In your favorite terminal, clone the project from GitHub

```shell
git clone https://github.com/progressively-crew/progressively
```

#### Create `.env` files for the `frontend` and `backend` packages

Progressively comes with two files called `.env.example` containing example values that **you have to modify.** Also Progressively only knows how to deal with `.env` files but not with `.env.example` ones.

With the following, you will copy the `.env.example` file into a `.env` one that Progressively will use.

```shell
$  cp ./packages/backend/.env.example ./packages/backend/.env
$  cp ./packages/frontend/.env.example ./packages/frontend/.env
```

#### Start Postgres

You can decide to install [Postgres](https://www.postgresql.org/download/) from its website or you can start it with docker using the following command:

```shell
# this will start Postgres in a local container with a dummy password.
# keep in mind that you can change the password BUT you will have to modify
$ docker run --name progressively-db -e POSTGRES_PASSWORD=admin -e POSTGRES_USER=admin -e POSTGRES_DB=progressively -p 5432:5432 -d postgres
```

#### Start Redis

You can decide to install [Redis](https://redis.io/) from its website or you can start it with docker using the following command:

```shell
$ docker run -it --rm --name progressively-redis -p 6379:6379 -d redis
```

{% hint style="info" %}
Redis is used to handle WebSockets at scale in case you want to start Progressively on multiple machines.
{% endhint %}

#### Setup the monorepo

The following command will install the project dependencies and create the links between the different packages of the monorepo:

```shell
$ pnpm run setup
```

#### Create Postgres tables

The following command will leverage [Prisma](https://www.prisma.io/) to create the tables that Progressively needs in Postgres. You should only have to run this command once.

```shell
$ pnpm run db:prepare
```

#### Start the backend & frontend project

At the project run, you can start the frontend and the backend project in dev mode:

```shell
$ pnpm run dev
```

The backend is now available locally at [http://localhost:4000](http://localhost:4000).



#### Follow the onboarding steps

Go to [http://localhost:3000/welcome](http://localhost:3000/welcome) and let you drive in the onboarding steps to create your Admin User and your first project.
