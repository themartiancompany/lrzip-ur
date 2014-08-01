# Maintainer: Alexander Rødseth <rodseth@gmail.com>
# Contributor: graysky <graysky AT archlinux DOT us>
# Contributor: kastor@fobos.org.ar

pkgname=lrzip
pkgver=0.616
pkgrel=2
pkgdesc='Multi-threaded compression using the rzip/lzma, lzo, and zpaq algorithms'
url='http://lrzip.kolivas.org/'
license=('GPL')
arch=('x86_64' 'i686')
depends=('lzo' 'bzip2' 'zlib' 'bash' 'gcc-libs')
source=("http://ck.kolivas.org/apps/$pkgname/$pkgname-$pkgver.tar.bz2")
sha256sums=('982d5a8db4d8bbbced6e33fbbcd589c9b3fc4275110155d7bd71cbeff4a235ae')

if [ "$CARCH" != "x86_64" ]
then
  makedepends+=('nasm')
  _flag="--enable-asm"
fi

build() {
  cd "$pkgname-$pkgver"

  CFLAGS="$CFLAGS -fomit-frame-pointer"
  CXXFLAGS="$CXXFLAGS -fomit-frame-pointer"
  ./autogen.sh --prefix=/usr "$_flag"
  make
}

check() {
  make -C "$pkgname-$pkgver" -k check
}

package() {
  make -C "$pkgname-$pkgver" DESTDIR="$pkgdir" install-strip
}

# vim:set ts=2 sw=2 et:
