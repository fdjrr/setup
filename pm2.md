# Installation

The latest PM2 version is installable with NPM or Yarn:

```bash
$ npm install pm2@latest -g
```

# Start an app

The simplest way to start, daemonize and monitor your application is by using this command line:

```bash
$ pm2 start app.js --name <app_name>
```

# Managing processes

Managing application state is simple here are the commands:

```bash
$ pm2 restart app_name
$ pm2 reload app_name
$ pm2 stop app_name
$ pm2 delete app_name
```