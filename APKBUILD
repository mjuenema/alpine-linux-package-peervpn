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
	peervpn.confd
	"

# peervpn has a strange versioning scheme.
builddir="$srcdir/$pkgname-0-044"

build() {

	# Must copy these into fakeroot?
	install -m 755 $pkgname.initd "$builddir"/$pkgname.initd
	install -m 755 $pkgname.confd "$builddir"/$pkgname.confd

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

	install -Dm644 $pkgname.confd "$pkgdir"/etc/conf.d/$pkgname \
		|| return 1
}

md5sums="3acb4cbf083c0bdacc90ad7d2403b1bc  peervpn-0-044.tar.gz
77e61c33f71e763dfa9a2fad32b1d613  peervpn.initd
d9a6c5b68a5c674460a0bf69fc6d3015  peervpn.confd"
sha256sums="4402d5ce956d95ff85b8aeb455d984b9eb9c2e6a058d2580c8e90da12fed8392  peervpn-0-044.tar.gz
8c9f9b711acf3e33f1f24e842e0f61ed1bdb5576dad4256cfbab0b65718f20eb  peervpn.initd
399805817f492fae83733a01cc09ef4db87f776995cc19361d8165dfe93ff9af  peervpn.confd"
sha512sums="7c9dcfd1822ef4d9c5954589b041f7165df93bb81a35fc8b741702aad738bd846718822bb47ba8ac0c23ece1c5f9170334a688c3670cc8bd199733e49aaf5067  peervpn-0-044.tar.gz
4becc336b8a646bfbcb6f0f2fc3db587c46128ffe312ce8fff928665bdfe66c333a81b6885a315b960ccaff9a1b7be5d00885b2369e0a1cbc0407e972fe81a47  peervpn.initd
b9a53f6ca0b0c125248995439558fcd50c5bceac04f4a3ac4cfc894d6a3ae9c4927dcee61c872a7c9c12311b01d5dc2cbbec989a88d8b826fb2cabcc18f05878  peervpn.confd"
