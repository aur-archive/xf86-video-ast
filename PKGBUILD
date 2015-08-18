# $Id: PKGBUILD 231243 2015-02-10 21:19:58Z lcarlier $
# Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=xf86-video-ast
pkgver=0.97.0
pkgrel=6
pkgdesc="X.org ASPEED AST Graphics video driver"
arch=(i686 x86_64)
url="http://xorg.freedesktop.org/"
license=('custom')
depends=('glibc')
makedepends=('xorg-server-devel' 'X-ABI-VIDEODRV_VERSION=19')
conflicts=('xorg-server<1.16' 'X-ABI-VIDEODRV_VERSION<19' 'X-ABI-VIDEODRV_VERSION>=20')
groups=('xorg-drivers' 'xorg')
source=(${url}/releases/individual/driver/${pkgname}-${pkgver}.tar.bz2 git-fix.diff)
sha256sums=('28fcd4781676485293f6dcd46e0797866f6219e22e1851c9796b037589998e76'
            '523911aacaf60a583ad3c306ba9e91ea6ea080d8285edccfc20e0cdd807b75a0')

prepare() {
  cd ${pkgname}-${pkgver}
  patch -Np1 -i ${srcdir}/git-fix.diff
}

build() {
  cd ${pkgname}-${pkgver}
  ./configure --prefix=/usr
  make
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install
  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/"
}
