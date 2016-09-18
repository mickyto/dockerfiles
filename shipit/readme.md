# Docker container for shipit

This docker consists of node.js and shipit-cli and useful for deploying node.js application

## Usage

The container requires `shipitfile.js` and [shipit-deploy](https://github.com/shipitjs/shipit-deploy) from your application source

```
docker run -t --rm -v yourAppDirName:/usr/src/app -v ~/.ssh:/root/.ssh shipit shipit staging deploy 
```

## Build container

docker build -t shipit .
