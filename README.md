heroku-buildpack-imagemagick
=================================

[![heroku buildpack](https://img.shields.io/badge/heroku-buildpack-blueviolet)](https://elements.heroku.com/buildpacks/)

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for vendoring the ImageMagick binaries into our application.

Cloned from https://github.com/StructionSite/heroku-buildpack-imagemagick and modified to fit our needs.

### Differences from [original ImageMagick configuration](https://www.imagemagick.org/script/resources.php)
- changed policy memory limit parameters
  - `disk` to 10GB
  - `memory` to 6GB
  - `map` to 4GB

### Install

Open a terminal and enter the following command:

`heroku buildpacks:add https://github.com/DriverReach/heroku-buildpack-imagemagick  --index 1 --app HEROKU_APP_NAME`

Note: "index 1" moves a buildpack to the top of the buildpack install order

### Changing version
Go to https://www.imagemagick.org/download/releases and find a version you want (*.tar.gz).
You can set the environment variable `IMAGE_MAGICK_VERSION` to the desired version (e.g. `6.9.10-59`).
Clear cache, as shown below, and redeploy your app to Heroku.

By default, the `bin/compile` script will look for the latest 6.x version from the releases page.

### Clear cache
Since the installation is cached you might want to clean it out due to config changes.

Using the [Heroku Builds CLI](https://github.com/heroku/heroku-builds)

1. `heroku plugins:install heroku-builds`
2. `heroku builds:cache:purge -a HEROKU_APP_NAME`
