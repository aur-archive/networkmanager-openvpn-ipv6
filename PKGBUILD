# $Id: PKGBUILD 178400 2013-02-21 06:19:50Z heftig $
# Maintainer: Ionut Biru <ibiru@archlinux.org>

pkgname=networkmanager-openvpn-ipv6
pkgver=0.9.8.4
pkgrel=2
pkgdesc="NetworkManager VPN plugin for OpenVPN"
arch=('i686' 'x86_64')
license=('GPL')
url="http://www.gnome.org/projects/NetworkManager/"
depends=("networkmanager>=${pkgver}" 'openvpn' 'gtk3' 'libgnome-keyring')
makedepends=('intltool')
optdepends=('network-manager-applet: GNOME frontends to NetWorkmanager')
conflicts=('networkmanager-openvpn')
install=networkmanager-openvpn.install
options=('!libtool')
source=(http://ftp.gnome.org/pub/GNOME/sources/NetworkManager-openvpn/0.9/NetworkManager-openvpn-${pkgver}.tar.xz
        ipv6.patch)
sha256sums=('af8c52b6a61af3c178eed1ea8f1d4704bea87331fde43deb3d4aafe1821e6687'
            '07e3087042a9f869a881b76c3e85d2398b759c767f41926b9fa614a9781293bf')

build() {
  cd NetworkManager-openvpn-${pkgver}
  patch -p0 < ../ipv6.patch
  ./configure --prefix=/usr \
  	--sysconfdir=/etc \
	--libexecdir=/usr/lib/networkmanager \
	--disable-static
  make CFLAGS=-Wno-error
}

package() {
  cd NetworkManager-openvpn-${pkgver}
  make DESTDIR="${pkgdir}" install
}
