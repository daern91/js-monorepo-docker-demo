### Readme
All below commands are to be executed from `root` folder.

#### Local install
1. Run `yarn` to install all dependencies, this installs them correctly both in root and links local dependencies together. The `postinstall` hook will also run `yarn tsc` to type-check and build files.
2. Run `yarn test` which runs both scripts `yarn w:a` and `yarn w:c` to run programs in `workspace-a` for `workspace-c`

#### Individual docker builds
1. Build `workspace-a` image with
```
docker build -t workspace-a --build-arg package_json="$(cat $(pwd)/package.json)" -f packages/Dockerfile-workspace-a ./packages/
```

2. Build `workspace-c` image with
```
docker build -t workspace-c  -f packages/Dockerfile-workspace-c ./packages/
```
#### Docker-compose
1. Build images with
```
docker-compose build --build-arg package_json="$(cat $(pwd)/package.json)"
```
2. Run `docker-compose up` or `docker-compose run workspace-<a|b>`