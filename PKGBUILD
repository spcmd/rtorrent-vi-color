# Maintainer:  nemesys <nemstar [at] zoho [dot] com>
# Contributor: randomize46 <randomize46 [at] gmail [dot] com>
# Contributor: tjwoosta <tjwoosta@gmail.com>
# Contributor: Lucky <archlinux@builds.lucky.li>
# Contributor: Ashren <edgar [at] archlinux [dot] us>
# Contributor: Gaetan Bisson <bisson@archlinux.org>
# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: spcmd (https://github.com/spcmd)

pkgname="rtorrent-vi-color-spcmd"
_pkgname="rtorrent"
pkgver=0.9.6
pkgrel=1
pkgdesc='Ncurses BitTorrent client based on libTorrent with vi like keybindings and color patch.'
url="http://libtorrent.rakshasa.no"
arch=('i686' 'x86_64')
license=('GPL')
depends=("curl" "libtorrent>=0.13.6" "xmlrpc-c" "libsigc++")
conflicts=("rtorrent-vi-color")
provides=("${_pkgname}")
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/rakshasa/${_pkgname}/archive/${pkgver}.tar.gz"
        "${_pkgname}-${pkgver}_vi_keybinding_tjwoosta.patch"
        "${_pkgname}-${pkgver}_color.patch"
        "${_pkgname}-${pkgver}_delete_torrent_key_binding.patch")
sha1sums=('27505081254618077c291eb1ee36bfb41f974834'
          'd35b53be6d1d5686c8a66ea821154e095e7a1556'
          '78429b5cf5976270dc1a55d8dc0ef4644675512b'
          'b63da5d87031048c65aca1590ca3799c7fc78228')

build() {
  cd "${srcdir}/${_pkgname}-${pkgver}"

  patch -uNp1 -i "${srcdir}/${_pkgname}-${pkgver}_vi_keybinding_tjwoosta.patch"
  patch -uNp1 -i "${srcdir}/${_pkgname}-${pkgver}_color.patch"
  patch -uNp1 -i "${srcdir}/${_pkgname}-${pkgver}_delete_torrent_key_binding.patch"

  sed '/AM_PATH_CPPUNIT/d' -i configure.ac
  ./autogen.sh

  export CXXFLAGS="${CXXFLAGS} -fno-strict-aliasing"
  ./configure \
    --prefix=/usr \
    #--enable-debug \
    #--with-xmlrpc-c \

  make
}

package() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
  install -Dm644 doc/rtorrent.rc  "${pkgdir}/usr/share/doc/rtorrent/rtorrent.rc"
}
