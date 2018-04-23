# Script generated with Bloom
pkgdesc="ROS - OpenCV 3.x"
url='http://opencv.org'

pkgname='ros-kinetic-opencv3'
pkgver='3.3.1_6'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('cmake'
'ffmpeg'
'jasper'
'libjpeg-turbo'
'libpng'
'libtiff'
'protobuf'
'python2'
'python2-numpy'
'v4l-utils'
'vtk'
'zlib'
)

depends=('ffmpeg'
'jasper'
'libjpeg-turbo'
'libpng'
'protobuf'
'python2'
'python2-numpy'
'ros-kinetic-catkin'
'vtk'
'zlib'
)

conflicts=()
replaces=()

_dir=opencv3
source=()
md5sums=()

prepare() {
    cp -R $startdir/opencv3 $srcdir/opencv3
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

