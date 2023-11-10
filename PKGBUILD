# Maintainer: Shuta4 <shuta4@proton.me>

_pkgname=slock
pkgname="s4-$_pkgname"
pkgver=1.4
pkgrel=1
pkgdesc="Simple X display locker custom build"
url="https://github.com/Shuta4/slock"
arch=('i686' 'x86_64' 'arm' 'armv7h' 'armv6h' 'aarch64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxrandr')
source=("https://github.com/Shuta4/$_pkgname/archive/refs/tags/$pkgver-$pkgrel.tar.gz")
sha256sums=('2818f82d82ab000ed3b401c538d9ff465e92e2032f74eed8b2cd0edabd2781d3')

provides=("${_pkgname}")
conflicts=("${_pkgname}")

prepare() {
  cd "$srcdir/$_pkgname-$pkgver-$pkgrel"
  sed \
	  -e 's/CPPFLAGS =/CPPFLAGS +=/g' \
	  -e 's/CFLAGS =/CFLAGS +=/g' \
	  -e 's/LDFLAGS =/LDFLAGS +=/g' \
	  -i config.mk
}

build() {
  cd "$srcdir/$_pkgname-$pkgver-$pkgrel"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "$srcdir/$_pkgname-$pkgver-$pkgrel"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
  install -Dm644 README.md "$pkgdir/usr/share/doc/$_pkgname/README.md"
}
