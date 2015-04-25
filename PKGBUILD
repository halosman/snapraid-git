# Maintainer: Robert Holak <rholak@gmail.com>
# Maintainer: Christopher Krooß <didi2002@web.de>
# Modified for personal use: Scott Dose
# Also modified to use
# Skip data integrity checks for git repository

pkgname=snapraid-git
_gitname=snapraid
pkgver=7.1
pkgrel=1
pkgdesc="SnapRAID is a backup program for disk arrays. It stores parity information of your data and it recovers from up to six disk failures."
url="http://snapraid.sourceforge.net/"
arch=('x86_64' 'i686')
license=('GPLv3')
depends=()
makedepends=('git' 'autoconf')
backup=("etc/snapraid.conf")
install='snapraid.install'
source=("git+https://github.com/amadvance/snapraid"
        "snapraid.install")
md5sums=('SKIP'
'f81b7d91b8cc61bea0744cbcf1c681fc')

pkgver() {
  cd "$_gitname"
  git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g' 
}

package() {
  # Copy from INSTALL in git directory
  cd "$_gitname"
 
 # Generate config file
 autoconf

 ./configure --prefix=${pkgdir}/usr

 make
 DESTDIR=${pkgdir} make install
         	 
}
