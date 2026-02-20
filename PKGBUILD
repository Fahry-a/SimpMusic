# Maintainer: yourname <youremail@example.com>
pkgname=simpmusic
pkgver=1.0.3
pkgrel=1
pkgdesc="SimpMusic - A music streaming app"
arch=('x86_64')
url="https://github.com/maxrave-dev/SimpMusic"
license=('unknown')
depends=('libnotify' 'nss' 'gtk3' 'xdg-utils' 'at-spi2-core' 'libxss' 'libxtst')
options=('!strip')

source=("${pkgname}_${pkgver}_amd64.deb::https://github.com/maxrave-dev/SimpMusic/releases/download/v${pkgver}/simpmusic_${pkgver}_amd64.deb")
sha256sums=('SKIP')

prepare() {
    cd "$srcdir"
    ar x "${pkgname}_${pkgver}_amd64.deb"

    if [ -f data.tar.xz ]; then
        tar xf data.tar.xz
    elif [ -f data.tar.gz ]; then
        tar xf data.tar.gz
    elif [ -f data.tar.zst ]; then
        tar xf data.tar.zst
    fi
}

package() {
    cd "$srcdir"

    # Salin seluruh /opt/simpmusic ke pkgdir
    install -dm755 "$pkgdir/opt"
    cp -r opt/simpmusic "$pkgdir/opt/simpmusic"

    # Buat symlink binary ke /usr/bin
    install -dm755 "$pkgdir/usr/bin"
    ln -sf /opt/simpmusic/bin/SimpMusic "$pkgdir/usr/bin/simpmusic"

    # Install desktop entry
    install -dm755 "$pkgdir/usr/share/applications"
    install -Dm644 opt/simpmusic/lib/simpmusic-SimpMusic.desktop \
        "$pkgdir/usr/share/applications/simpmusic.desktop"

    # Install icon
    install -dm755 "$pkgdir/usr/share/pixmaps"
    install -Dm644 opt/simpmusic/lib/SimpMusic.png \
        "$pkgdir/usr/share/pixmaps/simpmusic.png"
}
