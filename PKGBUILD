pkgname=cgminer-skein
_gitname=cgminer_skein
epoch=1
pkgver=5670.45cf92d
pkgver() {
  cd "$srcdir/$_gitname"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}
pkgrel=1
pkgdesc="This is a modified cgminer 3.7.3 software for Skeincoin and Maxcoin stratum mining."
arch=('i686' 'x86_64')
depends=('curl' 'libcl' 'libusbx' 'jansson' 'libusb-compat')
makedepends=('git')
optdepends=('ncurses: For ncurses formatted screen output'
            'opencl-nvidia: OpenCL implementation for NVIDIA'
            'opencl-catalyst: OpenCL implementation for AMD')
license=('GPL3')
url="git://github.com/reorder/cgminer_skein"
source=('adl_defines.h'
	'adl_sdk.h'
	'adl_structures.h'
	"git+https://github.com/reorder/cgminer_skein/")
md5sums=('209a8ce7e82441ec76624a045775684d'
	'7aa13bb4041400ada5e6b5d3904db5aa'
	'529466c93313d6f13923fc3c1c2027a9'
	'SKIP')
build() {
	cp "${srcdir}/adl_defines.h"		"${srcdir}/cgminer_skein/ADL_SDK/"
	cp "${srcdir}/adl_sdk.h"			"${srcdir}/cgminer_skein/ADL_SDK/"
	cp "${srcdir}/adl_structures.h"	"${srcdir}/cgminer_skein/ADL_SDK/"
	cd "${srcdir}/cgminer_skein"
	sh autogen.sh --enable-skein --enable-keccak --enable-scrypt --enable-opencl
	make
}
package_cgminer-skein() {
	cd "${srcdir}/cgminer_skein"
	make DESTDIR="$pkgdir/" install
}
