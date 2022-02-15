# Host multiple Create-React-App behind one NGINX 

Within this repository I'm trying to find out how to host the `production build` 
of multiple Create-React-App applications with one nginx.

Both apps where created like this:

```commandline
npx create-react-app app1
npx create-react-app app2
```

The production builds are produced like this (see `app1/Dockerfile`, `app2/Dockerfile`):

```commandline
npm run build
```

## About Docker
This example uses Docker-compose, but should also run without Docker.
So running additional Docker services (like another nginx) is not an option.


## Current state

Currently, this example only hosts one CRA app.

The stack (nginx+react) can be started with: 

```commandline
docker-compose up
```

Then, open browser, pointing to `http://localhost:${NGINX_PORT}`.
This will only show app1.

## GOAL

The goal is to be able to open each CRA-app using a separate URL:

* `http://localhost:${NGINX_PORT}/app1`
* `http://localhost:${NGINX_PORT}/app2`

All static resources should be loaded correctly from each root directory.