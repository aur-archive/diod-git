# Contributor: Andreas B. Wagner <AndreasBWagner@pointfree.net>
pkgname=diod-git
pkgver=791.171ac34
pkgrel=1
pkgdesc="A userspace I/O forwarding server that implements 9p2000.L"
arch=('i686' 'x86_64')
url="https://github.com/chaos/diod"
license=('GPL2')
groups=()
depends=('lua51' 'libcap')
makedepends=('git')
provides=('diod')
conflicts=()
replaces=()
backup=()
options=()
install=
source=("$pkgname::git+https://github.com/chaos/diod.git")
noextract=()
md5sums=('SKIP')

pkgver() {
  cd $srcdir/$pkgname
  echo $(git rev-list --count master).$(git rev-parse --short master)
}

build() {
  cd "$srcdir/$pkgname"
  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc --sbindir=/usr/bin CFLAGS=-O2 CPPFLAGS="-I/usr/include/lua5.1" --with-lua-suffix=5.1
  make
}

#check() {
#	cd "$srcdir/$pkgname"
#	make check
#}

package() {
  cd "$srcdir/$pkgname"
  make DESTDIR="$pkgdir/" install
  ln -s /usr/bin/diodmount $pkgdir/usr/bin/mount.diod
} 
