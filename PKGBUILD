# Maintainer: Alucryd <alucryd at gmail dot com>
# Contributor: Sebastian Lenz <sebastian@archusers.de>

_ext=user-theme
pkgname=gnome-shell-extension-${_ext}-git
pkgver=3.8.3.1.real.2
pkgrel=1
pkgdesc="Load shell themes from user directory"
arch=('any')
url="http://live.gnome.org/GnomeShell/Extensions"
license=('GPL' 'LGPL')
depends=('gnome-shell-extension-common-git')
makedepends=('git' 'gnome-common' 'intltool')
provides=("gnome-shell-extension-${_ext}")
conflicts=('gnome-shell-extensions-git' "gnome-shell-extension-${_ext}")
install=${pkgname%-*}.install
source=('git+http://git.gnome.org/browse/gnome-shell-extensions#branch=gnome-3-8')
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}"/gnome-shell-extensions

  git describe | sed 's|\(.*-.*\)-.*|\1|;s|-|.|g'
}

build() {
  cd "${srcdir}"/gnome-shell-extensions

  ./autogen.sh --prefix=/usr --disable-schemas-compile --enable-extensions=${_ext}
  make
}

package() {
  cd "${srcdir}"/gnome-shell-extensions/extensions/${_ext}

  make DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
