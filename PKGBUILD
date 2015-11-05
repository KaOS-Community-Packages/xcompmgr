pkgname=xcompmgr
pkgver=1.1.7
pkgrel=1
pkgdesc="Composite Window-effects manager for X.org"
arch=('x86_64')
url="http://xorg.freedesktop.org/"
license=('custom')
depends=('libxcomposite' 'libxdamage' 'libxrender' 'libxext')

source=(http://xorg.freedesktop.org/releases/individual/app/${pkgname}-${pkgver}.tar.bz2 fix_broken_shadows.diff)
sha256sums=('c8049b1a2531313be7469ba9b198d334f0b91cc01efc2b20b9afcb117e4d6892'
            'SKIP')
prepare() {
  cd ${pkgname}-${pkgver}
  # fix broken shadows in openbox - patch takern from https://bugs.freedesktop.org/show_bug.cgi?id=46285
  patch -Np0 -i ${srcdir}/fix_broken_shadows.diff
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