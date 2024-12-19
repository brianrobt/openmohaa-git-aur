# Maintainer: Self Denial <selfdenial@pm.me>
pkgname=openmohaa-git
_pkgname="${pkgname/-git/}"
pkgver=0.80.0.r151.g38427fa
pkgrel=1
pkgdesc="Open re-implementation of Medal of Honor: Allied Assault "
arch=('i686' 'x86_64')
url="https://github.com/openmoh/openmohaa"
license=('GPL2')
depends=('openal' 'sdl2' 'openjpeg2' 'libmad')
makedepends=('cmake' 'git' 'ninja')
conflicts=("${_pkgname}")
options=(!debug !lto)
source=("${_pkgname}::git+${url}.git")
sha256sums=('SKIP')

pkgver() {
  cd "${_pkgname}"
  git describe --tags --long --abbrev=7 | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd "${_pkgname}"
  [[ -d build ]] && rm -rf build
  mkdir build && cd build
  
  cmake -G Ninja ../ -DCMAKE_INSTALL_PREFIX="${pkgdir}/usr/" -DTARGET_LOCAL_SYSTEM=1 -DUSE_SYSTEM_LIBS=0
}

package() {
  cd "${_pkgname}"
  ninja -C build install
}

