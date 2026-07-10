# How to build lachouette

## Build a local version
```
make version
docker buildx build -f docker/main/Dockerfile -t ghcr.io/regishanna/lachouette:<version> --load .
```

## Export a local version to a tar
```
docker save ghcr.io/regishanna/lachouette:<version> > lachouette.tar
```

## Import a tar
```
docker load < lachouette.tar
```

## Build and export to github
```
make version
docker login ghcr.io -u regishanna -p <password>
docker buildx build -f docker/main/Dockerfile -t ghcr.io/regishanna/lachouette:<version> --push .
```

## Tag a github version to latest
```
docker pull ghcr.io/regishanna/lachouette:<version>
docker tag ghcr.io/regishanna/lachouette:<version> ghcr.io/regishanna/lachouette:latest
docker push ghcr.io/regishanna/lachouette:latest
```
