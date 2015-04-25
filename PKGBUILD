# Maintainer: Robert Holak <rholak@gmail.com>
# Maintainer: Christopher Krooß <didi2002@web.de>
# Modified for personal use: Scott Dose
# Also modified to use
# Skip data integrity checks for git repository

pkgname=snapraid-git
_gitname=snapraid
pkgver=v7.0.r204.g2c4321d
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
         '3c70324b14808d9271621e9f5c2779c1')

pkgver() {
  cd "$_gitname"
  git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g' 
}

build() {
   cd "$_gitname"
   
   # Generate config file
   ./autogen.sh

   ./configure --prefix=/usr
   make
}

check() {
   cd "${srcdir}/$_gitname"
   make check
}
package() {
 cd $_gitname
 
 DESTDIR=${pkgdir} make install
         	 
 # copy over example conf file to /etc/ directory
 install -m 0644 -D -p snapraid.conf.example ${pkgdir}/etc/snapraid.conf.example
}
