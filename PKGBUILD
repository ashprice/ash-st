# Maintainer:

pkgname=ash-st-git
_pkgname=st
pkver=0.8.4
pkgrel=1
epoch=1
pkgdesc="My st fork"
url='https://github.com/ashprice/ash-st'
arch=('i686' 'x86_64')
license=('MIT')
options=('zipman')
depends=('libxft libxft-bgra')
makedepends=('ncurses' 'libxext' 'git')
optdepends=('dmenu')
source=('git://github.com/ashprice/ash-st')
sha1sums=('SKIP')

provides=("${_pkgname}")
conflicts=("${_pkgname}")

pkgver() {
    cd "${_pkgname}"
    printf "%s.r%s.%s" "$(awk '/^VERSION =/ {print $3}' config.mk)" \
    "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
    cd $srcdir/${_pkgname}
    sed -i '/tic /d' Makefile
}

build() {
    cd "${_pkgname}"
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd "${_pkgname}"
    make PREFIX=/usr DESTDIR="${pkgdir}" install
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
    install -Dm644 .Xdefaults "${pkgdir}/usr/share/doc/${pkgname}/Xdefaults.example"
}
