_pkgname=gnome-screenshot
pkgname="${_pkgname}-kirito"
pkgver=3.36.0
pkgrel=1
pkgdesc="Take pictures of your screen"
url="https://github.com/kiritofeng/gnome-screenshot"
arch=(x86_64)
license=(GPL2)
depends=(gtk3 libcanberra)
makedepends=(git meson appstream-glib)
groups=(gnome)
conflicts=("gnome-screenshot")
source=("${_pkgname}::git+${url}.git")
sha256sums=("SKIP")

pkgver() {
  git -C "${_pkgname}" describe --tags | sed 's/-/+/g'
}

build() {
  arch-meson "$_pkgname" build
  ninja -C build
}

check() {
  meson test -C build --print-errorlogs
}

package() {
  DESTDIR="$pkgdir" meson install -C build
}

# vim:set ts=2 sw=2 et:

