## ENV on Each Version
version 3.5, 3.6
```
export COLMAP_VERSION=3.5
export DOCKERFILE=cuda10.2-devel-ubuntu18.04
export CUDA_ARCHITECTURES=70
```

version 

## Step to reproduce

0. Prepare CUDA-supported machine
1. Clone colmap repo
```
git clone https://github.com/Graffity-Technologies/colmap-docker.git
```
2. Prepare Dockerfile
Please check parent repo for each version of Dockerfile because contributers may test with only specific based image.
https://github.com/colmap/colmap/blob/3.8/docker/Dockerfile

3. Specify `COLMAP_VERSION` from [colmap tags](https://github.com/colmap/colmap/tags) and build colmap image. <br/>
Note that `CUDA_ARCHITECTURES` may vary. Please see [here](https://github.com/colmap/colmap/issues/1822) <br/>
```
docker build -t graffitytech/colmap:${COLMAP_VERSION}-${DOCKERFILE} \
--build-arg COLMAP_VERSION=${COLMAP_VERSION}  \
--build-arg CUDA_ARCHITECTURES=${CUDA_ARCHITECTURES}  \
--no-cache \
-f ${DOCKERFILE}.Dockerfile .
```

4. Login to dockerhub and push
```
docker login
docker push graffitytech/colmap:<VERSION>
```
