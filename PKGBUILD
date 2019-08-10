# Maintainer: Philip Müller <philm@manjaro.org>

_pkgbase=matcha-kde
_pkgname=("${_pkgbase}"{,'-wallpapers'}
          'kvantum-theme-matcha'
          'konsole-colorscheme-matcha'
          'yakuake-skin-matcha'
          'konversation-theme-matcha')
pkgname=("${_pkgname[@]/%/}")
pkgbase=${_pkgbase}
_commit=e328f4228bddd5b4ced97336906f509e1ecddddc
pkgver=20190810
pkgrel=1
arch=('any')
url="https://gitlab.com/cscs/${_pkgbase}"
license=('GPL3')
makedepends=('git')
options=('!strip')
source=("${pkgbase}::git+${url}.git#commit=$_commit"
        'fix-calamares-transparent-issue.patch')
sha256sums=('SKIP'
            '72aba6e6b99d50dba4be0f681e299ce88ddb91dda12816a84b744f9201741241')

pkgver() {
    date +%Y%m%d
}
	
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

package_matcha-kde() {
	pkgdesc="Matcha theme for KDE Plasma 5"
	depends=('plasma-workspace')
	optdepends=('papirus-icon-theme: for a more consistent and beautiful experience (recommended)'
	            'matcha-gtk-theme: for a consistent look in GTK applications'
	            'matcha-kde-wallpapers: matcha KDE wallpapers'
	            'kvantum-theme-matcha: matcha theme for Kvantum (recommended)'
	            'konsole-colorscheme-matcha: matcha theme for Konsole'
	            'yakuake-skin-matcha: matcha theme for Yakuake'
	            'konversation-theme-matcha: matcha theme for Konversation'
	            'matcha-firefox-theme: matcha theme for Firefox')
	provides=("${_pkgbase}")
	conflicts=("${_pkgbase}")
	install=${pkgbase}.install

	_install plasma aurorae color-schemes
}

package_matcha-kde-wallpapers() {
	pkgdesc="Matcha KDE wallpapers"
	provides=('matcha-kde-wallpapers')
	conflicts=('matcha-kde-wallpapers')

	_install wallpapers
}

package_kvantum-theme-matcha() {
	pkgdesc="Matcha theme for Kvantum"
	depends=('kvantum-qt5')
	provides=('kvantum-theme-matcha')
	conflicts=('kvantum-theme-matcha')

	_install Kvantum
}

package_konsole-colorscheme-matcha() {
	pkgdesc="Matcha theme for Konsole"
	depends=('konsole')
	provides=('konsole-colorscheme-matcha')
	conflicts=('konsole-colorscheme-matcha')

	_install konsole
}

package_yakuake-skin-matcha() {
	pkgdesc="Matcha theme for Yakuake"
	depends=('yakuake')
	provides=('yakuake-skin-matcha')
	conflicts=('yakuake-skin-matcha')

	_install yakuake
}

package_konversation-theme-matcha() {
	pkgdesc="Matcha theme for Konversation"
	depends=('konversation')
	provides=('konversation-theme-matcha')
	conflicts=('konversation-theme-matcha')

	_install konversation
}
