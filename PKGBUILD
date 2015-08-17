#Maintainer: Benjamin Chretien <chretien at lirmm dot fr>
pkgdesc="ROS - XML macro language."
url='http://www.ros.org/'

_name=xacro
pkgname=ros-groovy-xacro
pkgver=1.7.3
arch=('i686' 'x86_64')
pkgrel=2
license=('BSD')
makedepends=('ros-build-tools')
depends=()
_dir=${_name}
source=("$_dir"::"git://github.com/ros-gbp/${_name}-release.git"#tag=release/groovy/${_name}/${pkgver}-0)
md5sums=('SKIP')

build() {
    [ -f /opt/ros/groovy/setup.bash ] && source /opt/ros/groovy/setup.bash
    [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
    cd ${srcdir}/build
    /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}
    cmake ${srcdir}/${_dir} \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/groovy \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
    make
}

package() {
    cd "${srcdir}/build"
    make DESTDIR="${pkgdir}/" install
}
