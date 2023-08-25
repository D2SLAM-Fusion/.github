## D2SLAM-Fusion

> In-door and out-door swarm slam system frame work in UAV Group
>
> All the codes running on Jetson Orin & Xavier NX & PC

## Repository name rules

1. perception:  perception algorithm
2. control: all controller and planner
3. 3rd-party:
4. driver:  all devices' drivers



## Buildding details

### 3rdparty

#### OpenCV Jetson Orin

Jetson Orin use OpenCV4.5.4 initially. However, some contrib_libs are needed. Therefore you need to compile OpenCV4.5.4 from source code.

![orin_jetpack](profile/attachments/orin_jetpack.png)

Download

```shell
wget -O opencv.zip https://github.com/opencv/opencv/archive/refs/tags/4.5.4.zip \
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/refs/tags/4.5.4.zip
```

Compile

```shell
unzip opencv.zip \
unzip opencv_contrib.zip \
cd opencv-4.5.4 \ 
mkdir build \
cd build \
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local/ -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules -D CUDA_ARCH_BIN='8.7' -D WITH_CUDA=1 -D WITH_V4L=ON -D WITH_QT=ON -D WITH_OPENGL=ON -D CUDA_FAST_MATH=1 -D WITH_CUBLAS=1 -D OPENCV_GENERATE_PKGCONFIG=1 -D WITH_GTK_2_X=ON -D BUILD_PERF_TESTS=OFF -D BUILD_TESTS=OFF   .. \

make -j8 \
sudo make install

```



