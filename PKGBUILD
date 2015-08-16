# Contributor: Роман Кирилич (Roman Kyrylych) <roman@archlinux.org>
# Contributor: Aaron Griffin <aaron@archlinux.org>
# Contributor: Vinay S Shastry <vinayshastry@gmail.com>
# Maintainer: GordonGR <gordongr@freemail.gr>

pkgname=lib32-yasm
_pkgname=yasm
pkgver=1.2.0
pkgrel=2
pkgdesc="A rewrite of NASM to allow for multiple syntax supported (NASM, TASM, GAS, etc.), lib32"
arch=('x86_64')
license=('custom')
url="http://www.tortall.net/projects/yasm/"
depends=('yasm' 'lib32-glibc')
source=("http://www.tortall.net/projects/yasm/releases/${_pkgname}-${pkgver}.tar.gz")
options=('!libtool')
md5sums=('4cfc0686cf5350dd1305c4d905eb55a6')

build() {
cd ${srcdir}/${_pkgname}-${pkgver}
export CC="gcc -m32"
export CXX="g++ -m32"
export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"
./configure --prefix=/usr --libdir=/usr/lib32 --libexecdir=/usr/lib32
make
}

check() {
cd ${srcdir}/${_pkgname}-${pkgver}
make check
}

package() {
cd ${srcdir}/${_pkgname}-${pkgver}
make DESTDIR=${pkgdir} install
install -Dm644 COPYING ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
cd "$pkgdir/usr"
rm -rf {bin,include,share/man}/
}
