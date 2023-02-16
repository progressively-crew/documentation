---
description: Starting with control, practical for contributors
---

# Medium Start

{% hint style="info" %}
In this guide, you will install Postgres and Redis through [Docker](https://www.docker.com/). But you can run them directly on your machine if you prefer.
{% endhint %}

Open your favorite terminal and run the following:

```shell
# Get the project from github
$ git clone https://github.com/progressively-crew/progressively && cd progressively

# Copy the example env variable into real env variable (feel free to modify them)
$ cp ./packages/backend/.env.example ./packages/backend/.env
$ cp ./packages/frontend/.env.example ./packages/frontend/.env

# Run Postgres locally in Docker. You can choose to install it directly if you prefer
$ docker run --name progressively-db -e POSTGRES_PASSWORD=admin -e POSTGRES_USER=admin -e POSTGRES_DB=progressively -p 5432:5432 -d postgres

# # Run Redis locally in Docker. You can choose to install it directly if you prefer
$ docker run -it --rm --name progressively-redis -p 6379:6379 -d redis

# Setup the monorepo and prepare the Database table structure. It's a one-off command
$ pnpm run setup && pnpm run build && pnpm run db:prepare

# Start the project in development mode
$ pnpm run dev
```

Go to [http://localhost:3000/welcome](http://localhost:3000/welcome) and let you drive in the onboarding steps to create your Admin User and your first project.
