pkgname=plasma-pa
arch=('x86_64')
pkgver=5.10.4c
pkgrel=1
pkgdesc="PulseAudio based volume control Plasma widget."
url="https://projects.kde.org/projects/kdereview/plasma-pa"
license=('GPL' 'LGPL' 'FDL')
options=('!docs')
depends=('kconfigwidgets' 'kcoreaddons' 'ki18n' 'kdeclarative' 'plasma-framework' 'pulseaudio' 'glib2'
         'libcanberra' 'gconf')
makedepends=('pkg-config' 'extra-cmake-modules' 'kdoctools')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/ShalokShalom/${pkgname}/archive/${pkgver}.tar.gz")
md5sums=('5e60d82ce6a7e6467f08c1d75200db31')


prepare() {
  cd ${pkgname}-${pkgver}
}

build() {
  mkdir -p build
  cd build 
  
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_SKIP_RPATH=ON \
    -DKDE_INSTALL_LIBDIR=lib \
    -DKDE_INSTALL_SYSCONFDIR=/etc \
    -DKDE_INSTALL_QMLDIR=/usr/lib/qt5/qml \
    -DKDE_INSTALL_PLUGINDIR=/usr/lib/qt5/plugins \
    -DBUILD_TESTING=OFF 
  make 
}

package() {
  cd build
  
  make DESTDIR=${pkgdir} install
}
