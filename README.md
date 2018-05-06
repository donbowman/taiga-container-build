# taiga-container-build

Build taiga frontend/backend/events containers
with built-in support for OAUTH2 single-sign-on against
Google.

## Setup

Copy environment.sample to environment.
Fill in the values. You will need to create credentials
if you wish to use Google as an OAUTH2 provider in the
[console](https://console.developers.google.com/apis/credentials)

## Build

You can set an environment variable ```TAIGA_CONTAINER_REGISTRY```
to your container registry. E.g. if you:

```
export TAIGA_CONTAINER_REGISTRY=us.gcr.io/corp-202415/
docker-compose build
docker-compose push
```

then it will push the images to
```
us.gcr.io/corp-202415/taiga_backend
us.gcr.io/corp-202415/taiga_frontend
us.gcr.io/corp-202415/taiga_events
us.gcr.io/corp-202415/taiga_celeryworker
```

## License

All files licensed under the Apache 2.0
[License](https://www.apache.org/licenses/LICENSE-2.0)

