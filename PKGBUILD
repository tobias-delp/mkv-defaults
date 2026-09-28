pkgname=mkv-defaults
pkgver=1.0.0
pkgrel=1
pkgdesc="Interactively set default audio and subtitle tracks for MKV files"
arch=('any')
url="https://github.com/YOUR_USERNAME/mkv-defaults"
license=('MIT')
depends=('python' 'mkvtoolnix-cli')
source=('mkv-defaults')
sha256sums=('203a49e7696f42757aacf6339837580e83dadf2050d658609a0a9c7fc91b0575')

package() {
    install -Dm755 "$srcdir/mkv-defaults" "$pkgdir/usr/bin/mkv-defaults"
}
