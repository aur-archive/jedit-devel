# Contributor: [Vitaliy Berdinskikh](mailto:ur6lad@archlinux.org.ua) aka UR6LAD

# PKGBUILD edit mode http://code.pi.co.ua/jedit-pkgbuild
_pkgbuildver=3

pkgname=jedit-devel
pkgver=5.0.0
pkgrel=1
pkgdesc="Programmer's text editor"
arch=('any')
url="http://www.jedit.org"
license=('GPL')
depends=('java-runtime')
makedepends=('sed')
provides=('jedit')
conflicts=('jedit' 'jedit-pkgbuild')
backup=(usr/share/jedit/modes/catalog)
source=(http://downloads.sourceforge.net/jedit/jedit${pkgver}install.jar
		http://code.pi.co.ua/jedit-pkgbuild/downloads/pkgbuild-${_pkgbuildver}.xml
		jedit-bin jedit.desktop)
install=jedit.install
changelog=${pkgname}.ChangeLog.markdown

package() {
	mkdir -p $pkgdir/usr/bin
	mkdir -p $pkgdir/usr/share/java/jedit
	mkdir -p $pkgdir/usr/share/{applications,jedit/modes,pixmaps}
	mkdir -p $pkgdir/usr/share/man/man1

	cd $srcdir

	install jedit-bin $pkgdir/usr/bin/jedit
	install -m 644 jedit.1 $pkgdir/usr/share/man/man1/jedit.1
	install -m 644 jedit.desktop $pkgdir/usr/share/applications/jedit.desktop
	ln -s ../jedit/doc/jedit.png $pkgdir/usr/share/pixmaps/jedit.png

	cd installer
	tar xfj jedit-api.tar.bz2 -C $pkgdir/usr/share/jedit
	tar xfj jedit-macros.tar.bz2 -C $pkgdir/usr/share/jedit
	tar xfj jedit-program.tar.bz2 -C $pkgdir/usr/share/jedit
	mv $pkgdir/usr/share/jedit/jedit.jar $pkgdir/usr/share/java/jedit

	sed -e s:'</MODES>':'<MODE NAME="PKGBUILD"\t\tFILE="pkgbuild.xml"\n\t\t\t\tFILE_NAME_GLOB="PKGBUILD"/>\n\n</MODES>': \
			-i $pkgdir/usr/share/jedit/modes/catalog
	install -m 644 $srcdir/pkgbuild-${_pkgbuildver}.xml $pkgdir/usr/share/jedit/modes/pkgbuild.xml
}

md5sums=('d91c8879cbcc607b8f0688db4420b713'
         '3ebd666c3f75494521679777bd5228a7'
         'b86cfcc6aca31e5a28ca343397907da1'
         '65caaa7807c3f2b864a4edcb50e3ceca')
sha256sums=('24b7f10f012737d77fe4bfa6c7961fca978ad3dd410561efd1ca8ab796e0f6ad'
            '88ec2fff060de8e10a9c742a5ec62ea8fe36ba3e20c80378aeec659839608992'
            '67668acc3a63dd44e0d0f5f8ff24f5e27830a1a0a3de0e458fc1935c0a6c4d40'
            '023a04e170e9dae0ae3a78e2e06806d1b789bf4f0d5e2b71e9cca941354e34f0')
