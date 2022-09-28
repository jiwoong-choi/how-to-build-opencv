# OpenCV 4 Installation Guide
## Step 1: install required apt packages
```bash
sudo apt -y update
sudo apt -y upgrade
sudo apt -y install build-essential cmake pkg-config \
  libjpeg-dev libtiff5-dev libpng-dev \
  libavcodec-dev libavformat-dev libswscale-dev libavresample-dev \
  libdc1394-22-dev libxvidcore-dev libx264-dev ffmpeg \
  libxine2-dev libv4l-dev v4l-utils \
  libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev \
  libatlas-base-dev libeigen3-dev gfortran \
  python3-dev python3-numpy libtbb2 libtbb-dev
```
## Step 2: build and install
```bash
cd ~
mkdir OpenCV4
cd OpenCV4
git clone -b 4.5.1 https://github.com/opencv/opencv
git clone -b 4.5.1 https://github.com/opencv/opencv_contrib
cd opencv
mkdir build
cd build
cmake \
-D CMAKE_BUILD_TYPE=Release \
-D CMAKE_INSTALL_PREFIX=${HOME}/.local \
-D BUILD_WITH_DEBUG_INFO=OFF \
-D BUILD_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D WITH_TESTS=OFF \
-D WITH_PERF_TESTS=OFF \
-D BUILD_opencv_python3=ON \
-D OPENCV_ENABLE_NONFREE=ON \
-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D WITH_TBB=OFF \
..
make -j`nproc`
make install
sudo ldconfig
```
