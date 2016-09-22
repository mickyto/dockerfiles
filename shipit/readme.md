# Docker container with [shipit](https://github.com/shipitjs/shipit)

This docker consists of node.js and shipit-cli and useful for deploying node.js application

## Usage

The container requires `shipitfile.js` in a directory you are running deployment and server you deploy to knows public key of your user 

```
docker run -t --rm -v "$PWD"/shipitfile.js:/usr/src/app/shipitfile.js -v ~/.ssh:/root/.ssh mickyto/shipit shipit staging deploy 
```

## shipitfile example

```javascript
module.exports = function (shipit) {
    require('shipit-deploy')(shipit);

    shipit.initConfig({
        default: {
            workspace: '/tmp/git-monitor',
            deployTo: '/path/to/deploy',
            repositoryUrl: 'https://github.com/username/reponame.git',
            ignores: ['files', 'not', 'for', 'deploy'],
            keepReleases: 2,
            key: '~/.ssh/id_rsa',
            branch: 'master'
        },
        staging: {
            servers: 'user@domain.com'
        }
    });

    shipit.task('taskName1', function () {
        return shipit.remote('command you write here will be ran in your server');
    });
    
    shipit.task('taskName2', function () {
        return shipit.remote('command you write here will be ran in your server');
    });
    # You can add tasks name in the end of the command in Usage section
};
```