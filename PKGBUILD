# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# The following guidelines are specific to BZR, GIT, HG and SVN packages.
# Other VCS sources are not natively supported by makepkg yet.

# Maintainer: Pierre-Emmanuel Wulfman <pierre-emmanuel@wulfman.fr>
pkgname=ligo-git # '-bzr', '-git', '-hg' or '-svn'
pkgver=0.52.0.r0.a0a589179
pkgrel=1
pkgdesc="High Level Smart Contract Language for Tezos"
arch=(any)
url="https://gitlab.com/ligolang/ligo"
license=('MIT')
groups=('LigoLANG')
depends=(
	'libevdev'
	'perl'
	'pkg-config'
	'gmp'
	'hidapi'
	'm4'
	'libcap'
	'bubblewrap'
	'rsync'
	'python-jsonschema'
)
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}" 'ligo')
replaces=()
backup=()
options=()
install=
source=("git+https://gitlab.com/ligolang/ligo")
noextract=()
md5sums=('SKIP')

# Please refer to the 'USING VCS SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	cd "$srcdir/${pkgname%-git}"

# Git, tags available
	printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
	git checkout $(git tag  | grep -E '^[0-9]' | sort -V | tail -1)
}

build() {
	cd "$srcdir/${pkgname%-git}"
	make
}

package() {
	cd "$srcdir/${pkgname%-git}"
	make DESTDIR="$pkgdir/" install
}
