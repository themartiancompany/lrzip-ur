# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: graysky <graysky@archlinux.us>
# Contributor: <kastor@fobos.org.ar>

_pkg=lrzip
pkgname="${_pkg}"
pkgver=0.651
pkgrel=3
_pkgdesc=(
  'Multi-threaded compression'
  'with rzip/lzma, lzo, and zpaq'
)
_http="https://github.com"
_ns="ckolivas"
url="${_http}/${_ns}/${_pkg}"
license=(
  'GPL'
)
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'armv7l'
  'armv6l'
  'mips'
  'i686'
  'pentium4'
  'powerpc'
)
depends=(
  'lzo'
)
makedepends=(
  'git'
)
source=(
  "git+${url}#tag=v${pkgver}"
  "${_pkg}-${pkgver}-CVE-2018-5786.patch::${url}/commit/3495188cd8f2215a9feea201f3e05c1341ed95fb.patch"
)
sha256sums=(
  'SKIP'
  '8573ff8dd049c91cd0e6d754683e889ae439119cb9e738241dedd369c280a6fc'
)

prepare() {
  cd \
    "${_pkg}"
  patch \
    -Np1 < \
    "../${_pkg}-${pkgver}-CVE-2018-5786.patch"
}

build() {
  cd \
    "${pkgname}"
  CFLAGS="$CFLAGS -fomit-frame-pointer"
  CXXFLAGS="$CXXFLAGS -fomit-frame-pointer"
  ./autogen.sh \
    --prefix="/usr" \
    "$flags"
  make
}

check() {
  make \
    -C \
      "${_pkg}" \
    -k \
      check
}

package() {
  make \
    -C \
      "${_pkg}" \
    DESTDIR="${pkgdir}" \
    install-strip
}

# vim: ts=2 sw=2 et:
# getver: -u 3 github.com/ckolivas/lrzip/blob/master/ChangeLog

