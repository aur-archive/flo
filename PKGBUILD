# Maintainer: Stefan Husmann <stefan-husmann@t-online.de>
pkgname=flo  
pkgver=1.0
pkgrel=3
pkgdesc="A mind mapping application that is focused on building content quickly"
url="http://trac.geiseri.com/wiki/FloMain"
arch=('i686' 'x86_64')
license=('GPL')
depends=('qt4' 'hunspell')
source=(http://trac.geiseri.com/wiki/download/FloSrc.zip)
md5sums=('dde488fa8162f99908de11369fda8718')

build() {
  cd $srcdir/FloSrc
  sed -i s+-lhunspell+-lhunspell-1.3+ application/application.pro
  sed -i s+-lhunspell+-lhunspell-1.3+ tests/aspell/aspell.pro
  sed -i s+-lhunspell+-lhunspell-1.3+ tests/reports/reports.pro
  sed -i s+-lhunspell+-lhunspell-1.3+ tests/freemind/freemind.pro
  sed -i '19i#include <unistd.h>' library/sxfile/getusername.cpp
  qmake-qt4
  make 
}

package() {
  cd $srcdir/FloSrc
  make INSTALL_ROOT=$pkgdir install
  install -Dm644 lib/libflo.a $pkgdir/usr/lib/libflo.a
  install -Dm644 lib/libdocs.a $pkgdir/usr/lib/libdocs.a
}
