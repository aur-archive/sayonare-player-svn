pkgname=sayonare-player-svn
pkgver=405
pkgrel=1
pkgdesc="Linux music player written in C++. It supports all common audio files (like mp3, wav, flac, ogg...). The main focus is on managing your music library."
arch=('i686' 'x86_64')
url="http://code.google.com/p/sayonara-player/"
license=('GPL3')
depends=('qt' 'curl' 'taglib' 'gstreamer0.10')
makedepends=('subversion' 'cmake')
provides=(sayonara-player)
source=()
md5sum=()

_svntrunk="http://sayonara-player.googlecode.com/svn/trunk/"
_svnmod=sayonara-player

build() {
	cd $startdir/src
	if [ -d $_svnmod/.svn ]; then
		(cd $_svnmod && svn up)
	else
		svn co $_svntrunk --config-dir ./  $_svnmod
	fi

	svn export $_svnmod $_svnmod-build
	cd $_svnmod-build
	cmake .
	make || return 1
	make prefix=/usr DESTDIR=$startdir/pkg/ install
}
