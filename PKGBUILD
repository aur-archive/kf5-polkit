# Maintainer: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Pierre Schmitz <pierre@archlinux.de>

pkgname=kf5-polkit
pkgver=v0.103.0.r7.g3a5f879
pkgrel=1
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kdesupport/polkit-qt-1'
license=('LGPL')
pkgdesc="Qt5 wrapper around polkit-1 client libraries, used by kdelibs to provide the polkit-1 kauth backend and by KDE's polkit client"
depends=('polkit' 'qt5-base')
makedepends=('extra-cmake-modules' 'polkit' 'qt5-base')
conflicts=('kf5-polkit')
provides=('kf5-polkit')
source=('git://anongit.kde.org/polkit-qt-1.git#branch=qt5')
md5sums=('SKIP')

pkgver() {
  cd polkit-qt-1
  git describe --long | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}

prepare() {
  mkdir build
}

build() {
  cd build
  cmake ../polkit-qt-1 \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
