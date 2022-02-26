# Maintainer: Librewish <librewish@gmail.com?
# Contributer: Dan Johansen <strit@manjaro.org>

pkgname=greetd-qtgreet
_pkgname=QtGreet
pkgver=45.311c1c8
pkgrel=1
pkgdesc='Qt based greeter for greetd, to be run under wayfire or similar wlr-based compositors.'
arch=('aarch64' 'x86_64')
url="https://gitlab.com/marcusbritanicus/QtGreet"
license=(GPLv3)
depends=('qt5-base' 'wlroots' 'qt5-wayland' 'greetd' 'wlrootsqt')
optdepends=('wayfire' 'sway' 'mpvpaper')
makedepends=('meson' 'ninja' 'python' 'git')
provides=('qtgreet')
install=$pkgname.install
source=("git+https://gitlab.com/marcusbritanicus/QtGreet.git")
md5sums=('SKIP')

pkgver() {
  cd $_pkgname
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

prepare() {
  cd $_pkgname
  arch-meson .build --buildtype=release
}

build() {
  cd $_pkgname
  ninja -C .build -k 0 -j $(nproc)
}

package() {
  cd $_pkgname
  DESTDIR="$pkgdir" ninja -C .build install
  
  install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
