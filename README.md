# A Docker compose
In this repo there are 2 images and a docker-compose to build an environment for your apps, splitting the backend and the frontend into two different containers.

The two images are linked together by the docker-compose. The api is also linked to a postgresql database.

## Environment
The env variables are into ***.env*** file, if you want to use a custom one you must replace it here.

## Frontend
The first image is an official nginx image, with simply added a custom .conf file,
the .conf file defines a proxy for all the http requests that are to be handled by the backend, 
and for all the other requests will use the /var/www/html/ directory into the container.

There's also a ***./app/Dockerfiles/conf.d/app.template*** file, used for bind env variable in nginx configuration, as suggested in nginx docker doc.

The ***/var/www/html/*** directory is bound with the ***/app/dist directory*** (see the docker-compose).

## Backend
The second image is an official php image (with apache) with a custom .conf file, that define a vhost for the incoming requests.