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
docker build -t graffitytech/colmap:<VERSION> \
--build-arg COLMAP_VERSION=<VERSION>  \
--build-arg CUDA_ARCHITECTURES=75  \
--no-cache \
-f cuda11.7.0-devel-ubuntu22.04.Dockerfile .
```

4. Login to dockerhub and push
```
docker login
docker push graffitytech/colmap:<VERSION>
```