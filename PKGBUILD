# Maintainer: Alexander Rødseth <rodseth@gmail.com>
# Contributor: graysky <graysky AT archlinux DOT us>
# Contributor: kastor@fobos.org.ar

pkgname=lrzip
pkgver=0.612
pkgrel=2
pkgdesc="Multi-threaded compression using the rzip/lzma, lzo, and zpaq algorithms"
url="http://lrzip.kolivas.org/"
license=('GPL')
arch=('i686' 'x86_64')
depends=('lzo2' 'bzip2' 'zlib' 'bash' 'gcc-libs')
if [ "$CARCH" != "x86_64" ]
then
  depends+=('nasm')
  _flag="--enable-asm"
fi
options=('!libtool')
source=("http://ck.kolivas.org/apps/$pkgname/$pkgname-$pkgver.tar.bz2")
sha256sums=('2c309fb40766207f1deeb09e2431ae34db7e6d7a22d713c25efcc84ed8c52e97')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  CFLAGS="$CFLAGS -fomit-frame-pointer"
  CXXFLAGS="$CXXFLAGS -fomit-frame-pointer"
  ./autogen.sh --prefix=/usr "$_flag"
  make
}

check() {
  cd "$srcdir/$pkgname-$pkgver"

  make -k check
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir/" install-strip
}

# vim:set ts=2 sw=2 et:
