# Run in docker

Simple and fast setup of FSC.IO on Docker is also available.

## Install Dependencies

- [Docker](https://docs.docker.com) Docker 17.05 or higher is required
- [docker-compose](https://docs.docker.com/compose/) version >= 1.10.0

## Docker Requirement

- At least 7GB RAM (Docker -> Preferences -> Advanced -> Memory -> 7GB or above)
- If the build below fails, make sure you've adjusted Docker Memory settings and try again.

## Build fsc base environment image

Note that the Angle brackets are replaced with private information:

```bash
git clone http://dockerbuild:dockerbuild@gitlab.valicn.com/cpp/futureshareschian/fscio/fsc.git  --depth 1
cd fsc/
git checkout -b devlop origin/devlop
cd Docker/dev-gitlab/builder
docker build . -t fscio/builder:<version>
```
## Build fsc devlop environment image

```bash
git clone http://dockerbuild:dockerbuild@gitlab.valicn.com/cpp/futureshareschian/fscio/fsc.git 
cd fsc/
git checkout -b devlop origin/devlop
cd Docker/gitlab
```

If you would like to target a specific branch/tag, you may use a build argument. For example, if you wished to generate a docker image based off of the 1.0.0 tag, you could do the following(Note that the Angle brackets are replaced with private information):

```
docker build -t fscio/fsc:<fsc tag version> . --build-arg baseEnvDeocker=fscio/builder:<baseEnvDockerVersion> --build-arg branch=<tag branch>  --build-arg symbol=<core symbol name> --build-arg precision=<core symbol precision> --build-arg  gitlabAuthentication=<username:passwd> 
```

## Start nodfsc docker container only

```bash
docker run --name nodfsc -p 8888:8888 -p 9876:9876 -t fscio/fsc nodfscd.sh -e --http-alias=nodfsc:8888 --http-alias=127.0.0.1:8888 --http-alias=localhost:8888 arg1 arg2
```

Enjoy it, guys!
