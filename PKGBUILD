# Maintainer: Your Name <youremail@domain.com>
pkgname=mayu-git
pkgver=r4.96e8ab4
pkgrel=1
pkgdesc=""
arch=("x86_64")
url=""
license=('unknown')
groups=()
depends=('boost' 'libusb')
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=
source=('git+https://github.com/HiroakiMikami/mayu')
noextract=()
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/${pkgname%-git}"

  # Git, no tags available
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/${pkgname%-git}"
  ./configure
  make
}

package() {
  # Add systemd service
  cd "$startdir"
  mkdir -p "$pkgdir/usr/local"
  mkdir -p "$pkgdir/etc/systemd/system"
  cp ./mayud "$pkgdir/usr/local"
  cp ./mayu@.service "$pkgdir/etc/systemd/system/"

  # Install mayu
  cd "$srcdir/${pkgname%-git}"
  make prefix="$pkgdir/usr/local" install
}
