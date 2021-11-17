# Maintainer: Tom Hesse <heyhoman at mailbox dot org>
pkgname=4scanner-custom
_pkgname=4scanner
pkgver=r170.56422cb
pkgrel=1
pkgdesc="Command line tool to download images from multiple imageboards"
arch=('any')
url="https://github.com/Heyhoman/4scanner"
license=('MIT')
depends=('python>=3.0.0' 'python-requests>=2.20.0')
makedepends=('python-setuptools')
provides=('4scanner')
conflicts=('4scanner')
install=4scanner.install
source=($_pkgname::git+https://github.com/Heyhoman/4scanner)
sha256sums=('SKIP')

pkgver() {
	cd "$_pkgname"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/$_pkgname"
	python setup.py clean --all
	python setup.py build
}

package() {
	cd "$srcdir/$_pkgname"
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
	install -Dm644 README.md "$pkgdir/usr/share/doc/$_pkgname/README"
	install -Dm644 OPTIONS.md "$pkgdir/usr/share/doc/$_pkgname/OPTIONS"
	install -Dm644 example.json "$pkgdir/usr/share/doc/$_pkgname/example.json"
	install -Dm644 contrib/systemd/4scanner.service "$pkgdir/usr/lib/systemd/user/4scanner.service"
	python setup.py install --root "$pkgdir" --skip-build
}
