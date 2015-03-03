# Maintainer: Alexander Rødseth <rodseth@gmail.com>
# Contributor: graysky <graysky AT archlinux DOT us>
# Contributor: kastor@fobos.org.ar

pkgname=lrzip
pkgver=0.620
pkgrel=1
pkgdesc='Multi-threaded compression using the rzip/lzma, lzo, and zpaq algorithms'
url='http://lrzip.kolivas.org/'
license=('GPL')
arch=('x86_64' 'i686')
depends=('lzo' 'zlib')
source=("http://ck.kolivas.org/apps/$pkgname/$pkgname-$pkgver.tar.bz2")
sha256sums=('4d0b8738ad4fa253bc74080c465a67fb938255fabbaf167d1213bc76b3f43486')
makedepends_i686=('nasm')

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

# vim:set ts=2 sw=2 et:
