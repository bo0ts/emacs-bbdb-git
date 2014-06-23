# Maintainer: Philipp Moeller <bootsarhax@gmail.com>
pkgname=emacs-bbdb-git  
pkgver=0.0.0
pkgrel=1
pkgdesc="The Insidious Big Brother Database (from git)"
url="http://savannah.nongnu.org/projects/bbdb/"
arch=('i686' 'x86_64')
license=('GPL3')
depends=('emacs')
makedepends=('texinfo')
optdepends=('vm: The vm mailer for emacs')
provides=('bbdb=3.0')
conflicts=('bbdb')
changelog=ChangeLog
source=("$pkgname"::'git://git.savannah.nongnu.org/bbdb.git#branch=master')
md5sums=('SKIP')

# No usable tags in the repo
pkgver() {
  cd "$srcdir/repo"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build () {
  cd "$srcdir/$pkgname"
  ./autogen.sh
  ./configure --prefix=/usr \
              --with-lispdir=/usr/share/emacs/site-lisp/bbdb \
              --with-texmf-dir=/usr/share/texmf/tex/latex
  make all
}

package () {
  cd "$srcdir/$pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir" install
}
