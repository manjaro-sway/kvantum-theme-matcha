# Maintainer: Philip Müller <philm@manjaro.org>

_pkgbase=matcha-kde
_pkgname=('kvantum-theme-matcha')
pkgname=("${_pkgname[@]/%/}")
pkgbase=${_pkgbase}
_commit=e328f4228bddd5b4ced97336906f509e1ecddddc
pkgver=20200810
pkgrel=2
arch=('any')
url="https://gitlab.com/cscs/${_pkgbase}"
license=('GPL3')
makedepends=('git')
options=('!strip')
source=("${pkgbase}::git+${url}.git#commit=$_commit"
        'fix-calamares-transparent-issue.patch')
sha256sums=('SKIP'
            '72aba6e6b99d50dba4be0f681e299ce88ddb91dda12816a84b744f9201741241')

prepare() {
	cd "${pkgbase}"
	rm -r konversation/themes/papirus{,-dark}/src
	patch -p1 -i ../fix-calamares-transparent-issue.patch
}

_install() {
	cd "${pkgbase}"
	# shellcheck disable=SC2154
	install -d "${pkgdir}"/usr/share
	cp -r "$@" "${pkgdir}"/usr/share
}

package_kvantum-theme-matcha() {
	pkgdesc="Matcha theme for Kvantum"
	depends=('kvantum')
	provides=('kvantum-theme-matcha')
	conflicts=('kvantum-theme-matcha')

	_install Kvantum
}
