# Contributor: Markus Juenemann <markus@juenemann.net>
# Maintainer: Markus Juenemann <markus@juenemann.net>
pkgname=peervpn
pkgver=0.044
pkgrel=0
pkgdesc="PeerVPN builds virtual ethernet networks between multiple computers"
url="https://peervpn.net"
arch="all"
license="GPL3"
depends="libressl zlib"
makedepends="$depends libressl-dev zlib-dev linux-headers"
install=""
subpackages=""
source="
        http://${pkgname}.net/files/${pkgname}-${pkgver//./-}.tar.gz
	peervpn.initd
	"

# peervpn has a strange versioning scheme.
builddir="$srcdir/$pkgname-${pkgver//./-}"

build() {

	cd "$builddir"
	make
}

package() {
 	cd "$builddir"

	install -Dm755 $pkgname "$pkgdir"/usr/sbin/$pkgname \
		|| return 1

	install -Dm600 $pkgname.conf "$pkgdir"/etc/$pkgname.conf \
		|| return 1

	install -Dm755 ${srcdir}/$pkgname.initd "$pkgdir"/etc/init.d/$pkgname \
		|| return 1
}

md5sums="3acb4cbf083c0bdacc90ad7d2403b1bc  peervpn-0-044.tar.gz
c6c341d442888bbe583bf09e6fb67521  peervpn.initd"
sha256sums="4402d5ce956d95ff85b8aeb455d984b9eb9c2e6a058d2580c8e90da12fed8392  peervpn-0-044.tar.gz
a737637f4ab3767fb81cfef9cf4e0cb6fd57400df1caf028a2356b7ba4484def  peervpn.initd"
sha512sums="7c9dcfd1822ef4d9c5954589b041f7165df93bb81a35fc8b741702aad738bd846718822bb47ba8ac0c23ece1c5f9170334a688c3670cc8bd199733e49aaf5067  peervpn-0-044.tar.gz
50b40a4139499d384d0826a7449b19cd3fbe5869841461cd97e8a125518c3744a1a8c70445656c1a60dae4e2e4e3eb2331bf6b687c8886cb0075ed8ab45310bc  peervpn.initd"
