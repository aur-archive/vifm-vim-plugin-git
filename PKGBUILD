# Maintainer: Sial <NAME at cpan dot org>

_gitname='vifm'
pkgname=${_gitname}-vim-plugin-git
pkgver=0.7.5
pkgrel=2
pkgdesc="Ncurses based file manager with vi like keybindings, with vim plugin"
arch=('i686' 'x86_64')
url="https://github.com/ksteen/${_gitname}"
license=('GPL')
depends=('ncurses' 'gtk2')
makedepends=('git')
conflicts=('vifm', 'vifm-git')
install=${pkgname}.install
source=("git+https://github.com/ksteen/${_gitname}")
md5sums=('SKIP')

build() {
	msg "Starting make..."

	cd "${srcdir}/${_gitname}"
	./configure --prefix=/usr
	make
}

pkgver() {
	cd "${srcdir}/${_gitname}"
	cat README | grep 'Version:' | sed 's/^.*: //'
}

package() {
	cd "${srcdir}/${_gitname}"
	make DESTDIR=${pkgdir} install

	# vim plugin
	cd "${srcdir}/${_gitname}/data/vim"
	local installpath="$pkgdir/usr/share/vim/vimfiles"

	install -Dm644 doc/vifm.txt "$installpath/doc/vifm.txt"
	install -Dm644 ftdetect/vifm.vim "$installpath/ftdetect/vifm.vim"
	install -Dm644 ftplugin/vifm.vim "$installpath/ftplugin/vifm.vim"
	install -Dm644 plugin/vifm.vim "$installpath/plugin/vifm.vim"
	install -Dm644 syntax/vifm.vim "$installpath/syntax/vifm.vim"
}
