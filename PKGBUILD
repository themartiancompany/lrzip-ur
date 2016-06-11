# Maintainer: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: graysky <graysky@archlinux.us>
# Contributor: <kastor@fobos.org.ar>

pkgname=lrzip
pkgver=0.630
pkgrel=1
pkgdesc='Multi-threaded compression with rzip/lzma, lzo, and zpaq'
url='http://lrzip.kolivas.org/'
license=('GPL')
arch=('x86_64' 'i686')
depends=('lzo' 'zlib' 'bash' 'bzip2')
makedepends_i686=('nasm')
source=("http://ck.kolivas.org/apps/$pkgname/$pkgname-$pkgver.tar.bz2")
sha256sums=('2461f6bfa3231a98a76548741cbc64a2389e94eb5c3de152df8a118e23edd307')

build() {
  cd "$pkgname-$pkgver"

  CFLAGS="$CFLAGS -fomit-frame-pointer"
  CXXFLAGS="$CXXFLAGS -fomit-frame-pointer"

  if [[ $CARCH != x86_64 ]]; then
    ./autogen.sh --prefix=/usr --enable-asm
  else
    ./autogen.sh --prefix=/usr
  fi

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
