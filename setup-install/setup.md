# Setup

Once all dependencies have been installed, the rest of the setup process is quick.

After completing the steps below for the API, all that's left to do is run `npm run dev` in both the API and the CMS main folders.

### Prerequisites

[Docker](https://docs.docker.com/engine/installation/) \(version &gt;1.10.0\)  
[Docker Compose](https://docs.docker.com/compose/install/)

Start the Postgres and Redis services using the command: `docker-compose up --build -d`

This creates the needed containers, runs the database initialization script, gets the tables ready, and starts Redis.

Postgres runs on port 5432 and is exposed.

Redis runs on port 6379 and is exposed as well.

#### Configuration

The configuration file for Boldr is located inside the `.boldr` folder within your project root. The file is named `boldr.js`

In the config file there's quite a bit of behind the scenes customization you can make to your project. We'll cover that in a different section specifically related to the config.

There are additional values located in `src/config.js`.

These values either change frequently or contain secrets you won't want to publish to GitHub.

