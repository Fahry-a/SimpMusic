pkgname=simpmusic
pkgver=1.0.4
pkgrel=1
pkgdesc="SimpMusic - A music streaming app"
arch=('x86_64')
url="https://github.com/maxrave-dev/SimpMusic"
license=('GNU')
depends=('libnotify' 'nss' 'gtk3' 'xdg-utils' 'at-spi2-core' 'libxss' 'libxtst')
options=('!strip')

source=("${pkgname}_${pkgver}_amd64.deb::https://github.com/maxrave-dev/SimpMusic/releases/download/v${pkgver}/simpmusic_${pkgver}_amd64.deb")
sha256sums=('9b1c0502eddc01b5bf4624a96736c5bc9bbf92b0db9d73fca08c52b8e833cb7a')

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

    install -dm755 "$pkgdir/opt"
    cp -r opt/simpmusic "$pkgdir/opt/simpmusic"

    install -dm755 "$pkgdir/usr/bin"
    ln -sf /opt/simpmusic/bin/SimpMusic "$pkgdir/usr/bin/simpmusic"

    install -dm755 "$pkgdir/usr/share/applications"
    install -Dm644 opt/simpmusic/lib/simpmusic-SimpMusic.desktop \
        "$pkgdir/usr/share/applications/simpmusic.desktop"

    install -dm755 "$pkgdir/usr/share/pixmaps"
    install -Dm644 opt/simpmusic/lib/SimpMusic.png \
        "$pkgdir/usr/share/pixmaps/simpmusic.png"
}
