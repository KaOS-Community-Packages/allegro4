pkgname=allegro4
pkgver=4.4.2
pkgrel=1
pkgdesc="Portable library mainly aimed at video game and multimedia programming (legacy version)"
arch=('x86_64')
url="http://alleg.sourceforge.net/"
license=('custom')
depends=('sh' 'jack' 'libxpm' 'libxxf86vm' 'libxxf86dga' 'libxcursor')
makedepends=('cmake' 'libpng' 'mesa' 'glu')
options=('staticlibs')
source=(http://cdn.allegro.cc/file/library/allegro/${pkgver}/allegro-${pkgver}.tar.gz
        LICENSE)
md5sums=('4db71b0460fc99926ae91d223199c2e6'
         '7eea8dc56d1cf80f3bb6cb2992c2b9ef')

build() {
  cd "${srcdir}"
  mkdir build && cd build

  cmake "../allegro-${pkgver}" \
  	-DCMAKE_BUILD_TYPE=Release \
  	-DCMAKE_INSTALL_PREFIX=/usr \
	-DWANT_DOCS=OFF

  make
}

package() {
  cd "${srcdir}"/build

  make DESTDIR="${pkgdir}" install

  install -D -m644 "${srcdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
} 
