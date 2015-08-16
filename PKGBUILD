# Maintainer: Franck Michea <franck.michea@gmail.com>
pkgname=lpbm-git
pkgver=20121202
pkgrel=2
pkgdesc="Lightweight personal blog maker"
arch=("any")
url="http://bitbucket.org/kushou/lpbm"
license=("BSD")
groups=()
depends=("python" "python-markdown" "python-jinja" "python-pygments" "python-pyrss2gen")
makedepends=("git" "python-distribute")
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=()
noextract=()
md5sums=()

_gitroot="https://bitbucket.org/kushou/lpbm.git"
_gitname="lpbm"
_gitbranch="v2"

build() {
    if [ -d "$_gitname" ]; then
        cd "$_gitname"
        git checkout "$_gitbranch"
        git pull --rebase
    else
        git clone "$_gitroot" "$_gitname"
        cd "$_gitname"
        git checkout "$_gitbranch"
    fi

    python setup.py build
}

package() {
    cd "$_gitname"

    # Python package
    python setup.py install --root=$pkgdir/ --optimize=1

    # License
    mkdir -p $pkgdir/usr/share/licenses/$pkgname/
    install LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
