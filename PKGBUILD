# Maintainer:  Alberto Fanjul <albertofanjul@gmail.com>
# Contributor: Jonas Ådahl <jadahl@gmail.com>
# Contributor: Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Patrick Griffis <tingping@tingping.se>

pkgname=xdg-desktop-portal-gtk-git
pkgver=0.1.r401.gd3aea2d
pkgrel=1
pkgdesc="A GTK+ backend for xdg-desktop-portal"
url="https://github.com/flatpak/xdg-desktop-portal-gtk"
arch=(x86_64)
license=(LGPL2.1)
depends=(gtk3)
makedepends=(xdg-desktop-portal python git evince)
optdepends=("evince: Print preview")
provides=(xdg-desktop-portal-impl)
conflicts=(xdg-desktop-portal-gtk)
_branch=wip/screen-cast-window
source=("$pkgname::git+https://github.com/albfan/xdg-desktop-portal-gtk#branch=$_branch")
sha256sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd $pkgname
  NOCONFIGURE=1 ./autogen.sh
}

build() {
  cd $pkgname
  ./configure --prefix=/usr --libexecdir=/usr/lib
  make 
}

check() {
  cd $pkgname
  make check
}

package() {
  cd $pkgname
  DESTDIR="$pkgdir" make install
}
