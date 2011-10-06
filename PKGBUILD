# Maintainer: György Balló <ballogy@freestart.hu>
# Contributor: Roman Kyrylych <roman@archlinux.org>
# Contributor: Ben <ben@benmazer.net>

_pkgname=gtkspell
pkgname=${pkgname}3
pkgver=2.0.16
pkgrel=2
url="http://gtkspell.sourceforge.net/"
pkgdesc="GtkSpell provides word-processor-style highlighting and replacement of misspelled words in a GtkTextView widget"
arch=(i686 x86_64)
license=('GPL')
depends=(gtk3 enchant)
makedepends=(intltool gtk-doc)
options=(!libtool)
source=(http://gtkspell.sourceforge.net/download/$_pkgname-$pkgver.tar.gz
        gtk3_support.patch)
md5sums=(f75dcc9338f182c571b321d37c606a94
         c29be0667f59034b94bdd66e8f16b84c)

build() {
  cd "$srcdir/$_pkgname-$pkgver"

  # Add gtk3 support
  patch -Np1 -i $srcdir/gtk3_support.patch

  autoreconf -fi
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"

  make -C gtkspell DESTDIR="$pkgdir" install
}
