# Maintainer: trusktr <NAME at gmail dot com>

pkgname=otf-droidsansmono-powerline-git
pkgver=20130423
pkgrel=1
pkgdesc="Pre-patched and adjusted version of Droid Sans Mono for usage with the new Powerline plugin for vim."
arch=('any')
url='https://github.com/Lokaltog/powerline-fonts/tree/master/DroidSansMono'
license=('unknown')
depends=('fontconfig' 'xorg-font-utils')
makedepends=('git')
optdepends=('python-powerline-git: The ultimate statusline/prompt utility for vim.'
	'python2-powerline-git: The ultimate statusline/prompt utility for vim.')
install=${pkgname}.install
source=()
md5sums=('SKIP')

_gitroot='https://github.com/Lokaltog/powerline-fonts'
_gitname='powerline-fonts'

build() {
	cd "$srcdir"

	msg "Connecting to GIT server..."

	if [ -d "${srcdir}/${_gitname}" ]; then
		cd "$_gitname" && git pull origin
		cd "$srcdir"
		msg "The local files are updated."
	else
		git clone --depth=1 "$_gitroot" "$_gitname"
	fi

	msg "GIT checkout done or server timeout"
}

package() {
	cd "${srcdir}/${_gitname}/DroidSansMono"

	local font='Droid Sans Mono for Powerline.otf'
	install -Dm644 "$font" "${pkgdir}/usr/share/fonts/OTF/$font"
}
