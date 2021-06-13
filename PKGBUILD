# Maintainer: Aditya Gupta <ag15035 at gmail dot com>
pkgname=worldlinesim-git
pkgver=v1.271.0
pkgrel=1
pkgdesc="A simple Multiverse simulator written in C++, based on WorldLine Theory (Stein;s Gate)"
arch=('x86_64')
url="https://github.com/adi-g15/worldLineSim"
license=('MIT')
depends=()
makedepends=('gcc' 'git' 'cmake' 'ninja')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("${pkgname%-git}::git+https://github.com/adi-g15/worldlineSim#tag=${pkgver}")
md5sums=('SKIP')

prepare() {
#	if [[ ! -e "$srcdir/${pkgname%-git}" ]]; then
#		git clone https://github.com/adi-g15/worldLineSim "$srcdir/${pkgname%-git}" --depth=1
#	else
#		printf "$srcdir/${pkgname%-git} already exists ! Pulling latest commits...\n"
#		cd "$srcdir/${pkgname%-git}"
#		git pull
#	fi
	cd "$srcdir/${pkgname%-git}"

	git submodule update --init --depth=1
	cd ext/nanogui
	git submodule update --init --recursive --depth=1
}

build() {
	cd "$srcdir/${pkgname%-git}"
        mkdir -p build && cd build
        rm -f CMakeCache.txt
	cmake .. -G Ninja -DCMAKE_BUILD_TYPE=Release
	cmake --build .
}

package() {
	cd "$srcdir/${pkgname%-git}"
        cd build
	DESTDIR="$pkgdir/" cmake --install .
}
