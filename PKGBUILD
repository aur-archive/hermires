# Maintainer: lobotomius at gmail dot com

pkgname=hermires
pkgver=1.28
pkgrel=2
pkgdesc="Multiplatform c64 graphics editor"
arch=('any')
url="http://sourceforge.net/projects/hermires/"
license=('i686' 'x86_64')
depends=(allegro4)
source=('http://downloads.sourceforge.net/hermires/HermIRES-1.28.zip' 'hermires.patch')
md5sums=('c86759f9c43cb7f11d8b92b8a40a97ea'
         '48cabae3006f507ecac406df04ee850b')

build() {
	cd "$srcdir/HermIRES-$pkgver/source"
	patch -Np1 < "$srcdir/hermires.patch"
	make
}

package() {
	cd "$srcdir/HermIRES-$pkgver/source"
	chmod 755 ../HermIRES

	install -d "$pkgdir/usr/share/hermires/palettes"
	install -d "$pkgdir/usr/share/hermires/examples"

	install -D -m 755 ../HermIRES "$pkgdir/usr/bin/hermires"
	install -D -m 755 HermIRES.png "$pkgdir/usr/share/icons/HermIRES.png"
	install -D -m 755 HermIRES.desktop "$pkgdir/usr/share/applications/HermIRES.desktop"

	cd "$srcdir/HermIRES-$pkgver/palettes"
	for f in *; do
		install -m744 -t "$pkgdir/usr/share/hermires/palettes" "$f"
	done

	# install -D "$srcdir/HermIRES-$pkgver/examples/*.*" "$pkgdir/usr/share/hermires"
}
