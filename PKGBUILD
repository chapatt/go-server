# Maintainer: Chase Patterson <chapatt at gmail dot com>
pkgname=go-server
pkgver=17.12.0
pkgrel=1
pkgdesc='GoCD (continuous delivery) server'
arch=('any')
url='http://gocd.org'
license=('Apache')
source=("go-server-17.12.0-5626.zip::https://download.gocd.org/binaries/17.12.0-5626/generic/go-server-17.12.0-5626.zip"
	'go-server.service'
	'go-server.sysusers'
	'go-server.tmpfiles')
sha1sums=('5fe9b431923a58b67941fb55ad962dae57934b62'
	  'bb3561783b91ee898e68fd83933c311a60253f33'
	  '25b9e9bceac2f8fcd150e1bba36c984e16f8acf8'
	  'c45c1693a6325f01a3a4497472f375bbba78a82e')
depends=('java-runtime>=8')

package()
{
	install -dm755 "$pkgdir"/usr/share/go-server/
	install -dm755 -o 8154 -g 8154 "$pkgdir"/var/lib/go-server/

	install -Dm644 go-server.service \
		"$pkgdir"/usr/lib/systemd/system/go-server.service
	install -Dm644 go-server.sysusers \
		"$pkgdir"/usr/lib/sysusers.d/go-server.conf
	install -Dm644 go-server.tmpfiles \
		"$pkgdir"/usr/log/sysusers.d/go-server.conf

	cd $pkgname-$pkgver/
	install -Dm644 go-server.default "$pkgdir"/etc/default/go-server
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	install -Dm644 go.jar "$pkgdir"/usr/share/$pkgname/go.jar
	install -Dm755 server.sh "$pkgdir"/usr/share/$pkgname/server.sh
	install -Dm755 stop-server.sh "$pkgdir"/usr/share/$pkgname/stop-server.sh
}
