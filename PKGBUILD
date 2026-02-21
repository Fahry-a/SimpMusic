pkgname=simpmusic
pkgver=1.0.0
pkgrel=1
arch=('x86_64')
depends=('gtk3' 'libnotify')
source=('https://example.com/simpmusic-$pkgver.tar.gz')
sha256sums=('SKIP')

build() {
    cd "$srcdir/simpmusic-$pkgver"
    make
}

package() {
    cd "$srcdir/simpmusic-$pkgver"
    install -Dm755 simpmusic "$pkgdir/usr/bin/simpmusic"
}