# Merged with official ABS kwayland-integration PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Martin Stolpe <martin dot stolpe at gmail dot com>
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=kwayland-integration-git
pkgver=5.21.80_r164.gfdfaca8
pkgrel=1
pkgdesc='Provides integration plugins for various KDE frameworks for the wayland windowing system'
arch=($CARCH)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(kwindowsystem-git kidletime-git kwayland-git kguiaddons-git)
makedepends=(git extra-cmake-modules-git wayland-protocols)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(plasma-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
