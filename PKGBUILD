# Maintainer: piratecarrot <39475419+piratecarrot@users.noreply.github.com>
pkgname=openindy-git
pkgver=22.1.r25.gb22f4047
pkgrel=1
pkgdesc="An Open source software solution for industrial measurement"
arch=('i686' 'x86_64')
url="https://openindy.github.io/"
license=('LGPL3')
groups=('')
depends=('suitesparse')
makedepends=('make' 'gcc' 'qt5-base')
optdepends=('')
provides=('openindy')
conflicts=('openindy')
source=("${pkgname%-git}::git+https://github.com/OpenIndy/OpenIndy.git#branch=master")
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
	git submodule init
	git submodule update
	cd lib/OpenIndy-Core
	git submodule init
	git submodule update
#	patch --directory="${pkgname%-git}" --forward --strip=1 --input="$srcdir/build-fix.patch"
}

build() {
	cd "$srcdir/${pkgname%-git}"
	qmake openIndy.pro -r -spec linux-g++ CONFIG+=debug
	make	
}

package() {
	cd "$srcdir/${pkgname%-git}"
	make install
}
