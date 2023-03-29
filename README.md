## Step to reproduce

0. Prepare CUDA-supported machine
1. Clone colmap repo
```
git clone https://github.com/Graffity-Technologies/colmap-docker.git
```

2. Specify `COLMAP_VERSION` and build colmap image. <br/>
Note that `CUDA_ARCHITECTURES` may vary. Please see https://github.com/colmap/colmap/issues/1822 <br/>
```
docker build -t graffitytech/colmap:<VERSION> \
--build-arg COLMAP_VERSION=3.8  \
--build-arg CUDA_ARCHITECTURES=75  \
--no-cache \
-f cuda11.7.0-devel-ubuntu22.04.Dockerfile .
```

3. Login to dockerhub and push
```
docker login
docker push graffitytech/colmap:<VERSION>
```