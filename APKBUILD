# Contributor: Markus Juenemann <markus@juenemann.net>
# Maintainer: Markus Juenemann <markus@juenemann.net>
pkgname=peervpn
pkgver=0.044
pkgrel=0
pkgdesc="PeerVPN builds virtual ethernet networks between multiple computers"
url="https://peervpn.net"
arch="all"
license="GPL3"
depends="openssl zlib"
makedepends="$depends openssl-dev zlib-dev linux-headers"
install=""
subpackages=""
source="
        $url/files/$pkgname-0-044.tar.gz
	peervpn.initd
	"

# peervpn has a strange versioning scheme.
builddir="$srcdir/$pkgname-0-044"

build() {

	# Must copy these into fakeroot?
	install -m 755 $pkgname.initd "$builddir"/$pkgname.initd

	cd "$builddir"
	make
}

package() {
 	cd "$builddir"

	install -Dm755 $pkgname "$pkgdir"/usr/sbin/$pkgname \
		|| return 1

	install -Dm600 $pkgname.conf "$pkgdir"/etc/$pkgname.conf \
		|| return 1

	install -Dm755 $pkgname.initd "$pkgdir"/etc/init.d/$pkgname \
		|| return 1
}

md5sums="3acb4cbf083c0bdacc90ad7d2403b1bc  peervpn-0-044.tar.gz
c6c341d442888bbe583bf09e6fb67521  peervpn.initd
d9a6c5b68a5c674460a0bf69fc6d3015  peervpn.confd"
sha256sums="4402d5ce956d95ff85b8aeb455d984b9eb9c2e6a058d2580c8e90da12fed8392  peervpn-0-044.tar.gz
a737637f4ab3767fb81cfef9cf4e0cb6fd57400df1caf028a2356b7ba4484def  peervpn.initd
399805817f492fae83733a01cc09ef4db87f776995cc19361d8165dfe93ff9af  peervpn.confd"
sha512sums="7c9dcfd1822ef4d9c5954589b041f7165df93bb81a35fc8b741702aad738bd846718822bb47ba8ac0c23ece1c5f9170334a688c3670cc8bd199733e49aaf5067  peervpn-0-044.tar.gz
50b40a4139499d384d0826a7449b19cd3fbe5869841461cd97e8a125518c3744a1a8c70445656c1a60dae4e2e4e3eb2331bf6b687c8886cb0075ed8ab45310bc  peervpn.initd
b9a53f6ca0b0c125248995439558fcd50c5bceac04f4a3ac4cfc894d6a3ae9c4927dcee61c872a7c9c12311b01d5dc2cbbec989a88d8b826fb2cabcc18f05878  peervpn.confd"
