## $Id$
# Maintainer: TheKit <nekit1000 at gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=nemo-keepalive-git
pkgver=1.7.3.r0.gde8bf75
pkgrel=1
pkgdesc="CPU and display keepalive and scheduling library"
arch=('x86_64' 'aarch64')
url="https://git.sailfishos.org/mer-core/nemo-keepalive"
license=('GPL')
depends=('qt5-base' 'qt5-declarative' 'libiphb')
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=('git+https://git.sailfishos.org/mer-core/nemo-keepalive.git')
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
	cd "$srcdir/${pkgname%-git}"
	qmake
	make
	make -C lib-glib
	make -C tools
}

package() {
	cd "$srcdir/${pkgname%-git}"
	make INSTALL_ROOT="$pkgdir/" install
    make -C lib-glib install ROOT="$pkgdir/"
    make -C tools install ROOT="$pkgdir/"
}
