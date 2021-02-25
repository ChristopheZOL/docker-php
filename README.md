# docker-php

Manage DockerHub builds for php

The intended purpose of this repository is to provide branches and tags for a docker image with php and composer and some development tools

The latest version is for PHP 7.4.15, composer 2.0.9

## How to update

If you want to apply updates on this repository, checkout to the current tag you want to start with, create a new branch and apply your updates. Finally, tag the changes with a comprehensive changelog.

Before pushing your changes, make sure it works by building the image locally :

    docker build -t php:test .

## Rules to follow

- All versions must extend dockerfile official php image, no alpine allowed.
    
- PHP versions must be specific (`7.3.16` instead of only `7.3`)

## Notable facts

Installed packages : this image should be used for development only, it contains multiple packages that may not be needed for production. Use it at your own risk.

## Dockerhub

This project is built on [dockerhub, on ChristopheZOL account](https://hub.docker.com/repository/docker/zolweb/php-fpm). Images are free to use and come AS IS. I am not responsible for any mis-usage or any problem it may cause.

Automatic building is enabled, any tag push or master push trigger a build as following :

| Source | Type | Tag docker |
|:------:|:----:|:----------:|
| master | branch | latest |
| /^[0-9.]+/ | tag | {sourceref} |

Examples :
- Pushing the tag `7.3.16` gives the image `zolweb/php-fpm:7.3.16`
- Pushing the tag `7.4.4-composer-1.10.1` gives the image `zolweb/php-fpm:7.4.4-composer-1.10.1`
- Pushing to `master` updates the image `christophezol/php:latest`

You should not use `latest` tag, as the push order on this repository is done following my own needs, not PHP versions. Use tag instead.