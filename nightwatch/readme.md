# Docker container with [Nightwatch.js](http://nightwatchjs.org)

This docker consists of node.js and globally installed nightwatch and created for testing node.js application

## Usage

First you need to link [selenium container](https://hub.docker.com/r/selenium/standalone-firefox/) to your app container

```
docker run -d -P --name selenium --link <yourappcontainer>:app selenium/standalone-firefox
```

Then to run tests getting access to both application and selenium containers.
Note that command below requires you run it from your application's working directory and `package.json` contains test script  

```
docker run --rm --link selenium -v "$PWD":/usr/src/app -w /usr/src/app mickyto/nightwatch npm test
```
