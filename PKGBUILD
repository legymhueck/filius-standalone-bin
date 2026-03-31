# Maintainer: Robert Ulmer <arch.x(at)frontexpers.com>
pkgname="filius"
pkgver="2.10.1"
pkgrel=1
pkgdesc="Educational network simulation program for learning TCP/IP and computer networking concepts"
arch=('any')
url="https://www.lernsoftware-filius.de"
license=('GPL-2.0-or-later' 'GPL-3.0-or-later')
depends=('java-runtime>=17')
makedepends=('unzip')
source=(
    "filius"
	"https://www.lernsoftware-filius.de/downloads/Setup/$pkgname-$pkgver.zip"
    "filius.png"
    "filius.xml"
    "filius.desktop"
)
b2sums=('46d1ca720beaca66c3cee19e24487a1468f361751daed1705161edf8b61b05a699a9077252c330d13176342930fa414b1628a790b996a8cf275ef6ac6dab5f6b'
        '23db275c72cbae3814508ac8e87a5dfc6e8e2a48eac8984dcb2f5fde5d9b950abba733833e355390673b88ecbe4e56618bbd0245cc609a73725a6b9a22492c74'
        '2b000e42027082d7e194ba5ba0e829db5f89b310233bd3bdc732ccf3c176602a3b82f3c82dde137a7d3795145b525747ba6154118a4d48d4d89907edfd559eb1'
        'c219fd70872d79ad4d60fda99cf5157aa7b70ee271f6c29de26b4ee72de910cbb2142c434a4363bbc42be9482d9cbdb16041a073317ada24a5321296472b5ee2'
        '2cc5ed3f28a1b4ac58e56f785eef881f053396b9dc6984139321c12d32b81bb1a2708a53d1224f8ca22014dad750a674c54449c24db9e33cc694432c98befc4d')

package() {
	cd "$srcdir"

	# Application files
	install -dm755 "$pkgdir/usr/share/$pkgname"
	install -Dm644 filius.jar "$pkgdir/usr/share/$pkgname/filius.jar"
	install -Dm755 filius.sh "$pkgdir/usr/share/$pkgname/filius.sh"

	# Subdirectories with data files (config, help, images, libs, templates)
	local _datadir="$pkgdir/usr/share/$pkgname"
	for _dir in config hilfe img lib tmpl; do
		find "$_dir" -type d -exec install -dm755 "$_datadir/{}" \;
		find "$_dir" -type f -exec install -Dm644 "{}" "$_datadir/{}" \;
	done

	# Documentation and Licenses
	install -Dm644 -t "$pkgdir/usr/share/licenses/$pkgname" GPLv2.txt GPLv3.txt
	install -Dm644 -t "$pkgdir/usr/share/doc/$pkgname" Changelog.md Einfuehrung_Filius.pdf Introduction_Filius.pdf

	# Executable wrapper script
	install -Dm755 "filius" "$pkgdir/usr/bin/filius"

	# Application icon
	install -Dm644 "filius.png" "$pkgdir/usr/share/pixmaps/filius.png"

	# MIME type definition
	install -Dm644 "filius.xml" "$pkgdir/usr/share/mime/packages/filius.xml"

	# Desktop entry
	install -Dm644 "filius.desktop" "$pkgdir/usr/share/applications/filius.desktop"
}
