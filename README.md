# A Docker compose
In this repo there are 2 images and a docker-compose to build an environment for your apps, splitting the backend and the frontend into two different containers.

The two images are linked together by the docker-compose that also exposes a postgresql database.

By default the applications name will be "***appname***", if you want to use a custom one you must replace all the "***appname***" in:
- ***./docker-compose*** 
- ***./app/Dockerfiles/conf.d/app.conf*** 

## Environment
The env variables are into - ***.env*** file.
 The *** application.env ** is used for the domain name.
 The *** postgresql.env ** is used for the postgresql container.

## Frontend
The first image is an official nginx image, with simply added a custom .conf file,
the .conf file defines a proxy for all the http requests that will be prefixed by "api."
and for all the other requests will use the /var/www/html/ directory into the container.

The ***/var/www/html/*** directory is bound with the ***/app/dist directory*** (see the docker-compose).

## Backend
The second image is an official php image (with apache) with a custom .conf file, that define a vhost for the incoming requests.