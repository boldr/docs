# Setup

Once all dependencies have been installed, the rest of the setup process is quick.

After completing the steps below for the API, all that's left to do is run `npm run dev` in both the API and the CMS main folders.

### API

Enter the directory where your API lives.

Start the Postgres and Redis services using the command: `docker-compose up --build -d`

This creates the needed containers, runs the database initialization script, gets the tables ready, and starts Redis.

#### Configuration

Copy the `boldrrc.example` file or create a new file named `.boldrrc`

Copy and paste the `.boldrrc` values below, into your file. Make sure to change anything to fit your environment.

```
{
  "server": {
    "port": 2121,
    "host": "127.0.0.1"
  },
  "db": {
    "url": "postgres://postgres:password@localhost:5432/boldr"
  },
  "redis": {
    "url": "redis://127.0.0.1:6379/1"
  },
  "token": {
    "secret": "tokenissecret"
  },
  "mail": {
    "host": "mail.server.example.com",
    "user": "email@address.com",
    "password": "mailpassword",
    "from": "email@address.com"
  },
  "logging": {
    "level": "debug",
    "file": {
      "enabled": false
    }
  }
}
```

There are additional values located in `src/config.js`. 

These values either change frequently or contain secrets you won't want to publish to GitHub.



