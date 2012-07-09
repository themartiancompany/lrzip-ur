# Maintainer: Alexander Rødseth <rodseth@gmail.com>
# Contributor: graysky <graysky AT archlinux DOT us>
# Contributor: kastor@fobos.org.ar

pkgname=lrzip
pkgver=0.613
pkgrel=1
pkgdesc="Multi-threaded compression using the rzip/lzma, lzo, and zpaq algorithms"
url="http://lrzip.kolivas.org/"
license=('GPL')
arch=('x86_64' 'i686')
depends=('lzo2' 'bzip2' 'zlib' 'bash' 'gcc-libs')
if [ "$CARCH" != "x86_64" ]
then
  makedepends+=('nasm')
  _flag="--enable-asm"
fi
options=('!libtool')
source=("http://ck.kolivas.org/apps/$pkgname/$pkgname-$pkgver.tar.bz2")
sha256sums=('70dc55fbc4fe3d029c8edfc20f47f02d78c9c4c473201e6ec616febe9ce6b7eb')

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
