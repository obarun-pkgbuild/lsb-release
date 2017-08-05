# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://git.archlinux.org/svntogit/community.git/tree/trunk?h=packages/lsb-release
# 						Maintainer: Sven-Hendrik Haase <sh@lutzhaase.com>
# 						Contributor: Malte Rabenseifner <malte@zearan.de>
# 						Contributor: John Gerritse <reaphsharc@gmail.com>

pkgname=lsb-release
pkgver=1.4
pkgrel=15
pkgdesc="LSB version query program"
arch=(any)
url="http://www.linuxbase.org/"
license=('GPL2')
depends=('bash')
install=lsb-release.install
source=(http://downloads.sourceforge.net/lsb/$pkgname-$pkgver.tar.gz
		lsb_release_description.patch)
md5sums=('30537ef5a01e0ca94b7b8eb6a36bb1e4'
		'72f562d8eaa8915ab85fba13e68c8d68')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd "$srcdir/$pkgname-$pkgver"

  patch -Np0 < "$srcdir/lsb_release_description.patch"

  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  install -dm755 "$pkgdir/etc"
  echo "LSB_VERSION=$pkgver" >> "$pkgdir/etc/lsb-release"
  echo "DISTRIB_ID=Obarun" >> "$pkgdir/etc/lsb-release"
  echo "DISTRIB_RELEASE=rolling" >> "$pkgdir/etc/lsb-release"
  echo "DISTRIB_DESCRIPTION=\"Obarun Linux\"" >> "$pkgdir/etc/lsb-release"

  install -Dm 644 lsb_release.1.gz "$pkgdir/usr/share/man/man1/lsb_release.1.gz"
  install -Dm 755 lsb_release "$pkgdir/usr/bin/lsb_release"
}
