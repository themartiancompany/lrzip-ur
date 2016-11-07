# Maintainer: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: graysky <graysky@archlinux.us>
# Contributor: <kastor@fobos.org.ar>

pkgname=lrzip
pkgver=0.631
pkgrel=1
pkgdesc='Multi-threaded compression with rzip/lzma, lzo, and zpaq'
url='http://lrzip.kolivas.org/'
license=('GPL')
arch=('x86_64' 'i686')
depends=('lzo' 'zlib' 'bash' 'bzip2')
makedepends_i686=('nasm')
source=("http://ck.kolivas.org/apps/$pkgname/$pkgname-$pkgver.tar.bz2")
sha256sums=('0d11e268d0d72310d6d73a8ce6bb3d85e26de3f34d8a713055f3f25a77226455')

build() {
  cd "$pkgname-$pkgver"

  CFLAGS="$CFLAGS -fomit-frame-pointer"
  CXXFLAGS="$CXXFLAGS -fomit-frame-pointer"

  [ $CARCH != x86_64 ] && flags='--enable-asm'
  ./autogen.sh --prefix=/usr "$flags"
  make
}

check() {
  make -C "$pkgname-$pkgver" -k check
}

package() {
  make -C "$pkgname-$pkgver" DESTDIR="$pkgdir" install-strip
}

# getver: -u 3 github.com/ckolivas/lrzip/blob/master/ChangeLog
# vim:set ts=2 sw=2 et:
