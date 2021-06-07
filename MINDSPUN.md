# Mindspun

## Setup
git remote add upstream git@github.com:TryGhost/Admin.git

nvm use lts/fermium
rm -rf node_modules
yarn global add knex-migrator grunt-cli ember-cli
yarn install

## Update ghost-admin
Go to the ghost-admin/Admin repo:
```shell
git checkout main
git pull upstream main
git push # push upstream changes to our main branch
git checkout <COMMIT> -b <TAG>  # e.g. v4.2.0
git checkout steady
git merge <TAG>
```

* Check that .github directory is empty then continue.

```
git tag <TAG> # e.g. v4.2.0-1
git push && git push --tags
```

* Verify the submodule is on the right commit and go back to the top of the Ghost repo.


Ghost:
```shell
git checkout main
git pull upstream main
git push # push upstream changes to our main branch
git checkout <COMMIT> -b <TAG>  # e.g. v4.2.0
git checkout steady
git merge <TAG>
```
During merge:
* add content/themes/casper and core/client
* resolve package.json
* ... and any others.

```shell
cd core/client
git pull
cd ../..
```

Finally:
* update package.json to new version e.g. 4.6.6-2
* commit all (including core/client)

### General notes

To use the upstream version of a file:
```shell
git checkout --theirs /path/to/file
```


### Testing admin
```shell
nvm use lts/fermium
rm -rf node_modules
yarn install
ember test
```

### Testing Ghost
```shell
grunt test-all
```

## Build
```shell
grunt release
```
