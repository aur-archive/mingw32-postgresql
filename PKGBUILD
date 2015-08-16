pkgname=mingw32-postgresql
pkgver=9.1.3
pkgrel=2
pkgdesc="A sophisticated object-relational DBMS (mingw32)"
arch=('any')
url="http://www.postgresql.org/"
license=('custom:PostgreSQL')
depends=(mingw32-runtime)
makedepends=('mingw32-gcc')
options=('!strip' '!buildflags' '!libtool')
source=("http://ftp.postgresql.org/pub/source/v$pkgver/postgresql-$pkgver.tar.bz2")
md5sums=('641e1915f7ebfdc9f138e4c55b6aec0e')

build() {
  cd "${srcdir}/postgresql-$pkgver"
  unset LDFLAGS
  mkdir -p build && cd build
  ../configure \
  --prefix=/usr/i486-mingw32 \
  --host=i486-mingw32
  make
}

package() {
  cd "${srcdir}/postgresql-$pkgver"

  make DESTDIR=${pkgdir} install
  mv $pkgdir/usr/i486-mingw32/lib/*.dll "$pkgdir/usr/i486-mingw32/bin"
  i486-mingw32-strip $pkgdir/usr/i486-mingw32/bin/*.exe
  i486-mingw32-strip -x $pkgdir/usr/i486-mingw32/bin/*.dll
  i486-mingw32-strip -x $pkgdir/usr/i486-mingw32/lib/postgresql/*.dll
  i486-mingw32-strip -g $pkgdir/usr/i486-mingw32/lib/*.a
  rm -rf "$pkgdir/usr/i486-mingw32/lib/postgresql/pgxs"
}