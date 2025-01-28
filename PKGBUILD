# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024,2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.


# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: graysky <graysky@archlinux.us>
# Contributor: <kastor@fobos.org.ar>

_arch="$( \
  uname \
    -m)"
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
  local \
    _cflags=() \
    _cxxflags=()
  _cflags+=(
    $CFLAGS
    -fomit-frame-pointer
  )
  _cxxflags+=(
    $CXXFLAGS
    -fomit-frame-pointer
  )
  if [[ "${_arch}" != "x86_64" ]]; then
    _cxxflags+=(
      -DNOJIT 
    )
  fi
  cd \
    "${pkgname}"
  export \
    CFLAGS="${_cflags[*]}" \
    CXXFLAGS="${_cxxflags[*]}"
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

