# Maintainer: Aditya Gupta <ag15035 at gmail dot com>
pkgname=worldlinesim-git
pkgver=1
pkgrel=2
pkgdesc="A simple Multiverse simulator written in C++, based on WorldLine Theory (Stein;s Gate)"
arch=('x86_64')
url="https://github.com/adi-g15/worldLineSim"
license=('MIT')
depends=('libx11')
makedepends=('gcc' 'git' 'cmake' 'ninja')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("${pkgname%-git}::git+https://github.com/adi-g15/worldlineSim")
md5sums=('SKIP')

pkgver() {
        cd "$srcdir/${pkgname%-git}"

	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/${pkgname%-git}"
	cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
	cmake --build .
}

package() {
	cd "$srcdir/${pkgname%-git}"
        cd build
	DESTDIR="$pkgdir/" cmake --install .
}
