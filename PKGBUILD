# Maintainer: Stefan Husmann <stefan-husmann@t-online.de>
pkgname=emacs-ess-svn
pkgver=6048
pkgrel=2
pkgdesc="Emacs Speaks Statistics: A Universal Interface for \
 Statistical Analysis - svn-version"
arch=('any')
url="http://ess.r-project.org/"
license=('GPL')
depends=('emacs' 'r')
makedepends=('subversion' 'texlive-latexextra' 'texlive-plainextra')
provides=('ess' 'emacs-ess')
replaces=('ess-svn')
conflicts=('emacs-ess')
install=ess.install
options=('docs' '!makeflags')
source=('emacs-ess::svn+https://svn.r-project.org/ESS/trunk/')
md5sums=('SKIP')
_svnmod=emacs-ess

pkgver() {
  cd "$srcdir"/$_svnmod
  svnversion | sed 's+:+.+' | tr -d [A-z] 
}

build() {
  cd $srcdir/$_svnmod/
  make prefix=/usr
}

package() {
  cd $srcdir/$_svnmod
  make DESTDIR=$pkgdir/usr LISPDIR=$pkgdir/usr/share/emacs/site-lisp/ess \
    INFODIR=$pkgdir/usr/share/info/ install
}
