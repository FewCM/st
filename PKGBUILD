# Maintainer: SW
pkgname=st-fewcm
pkgver=0.8.4.r11.4dfa269
pkgrel=1
pkgdesc="A heavily-patched and customized build of st"
arch=(x86_64)
url="https://github.com/FewCM/st.git"
license=('MIT')
groups=()
depends=(libx11 libxinerama freetype2)
makedepends=(make)
checkdepends=()
optdepends=()
provides=(st)
conflicts=(st)
replaces=()
backup=()
options=()
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
  cd "${_pkgname}"
  printf "0.8.4.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

#prepare() {
#	cd dwm
#}

#build() {
#  cd dwm
#  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
#  flexipatch-finalizer.sh -o "${srcdir}/dwm" -d "${srcdir}/dwm" -r --debug
#}

package() {
  cd st
  mkdir -p ${pkgdir}/opt/${pkgname}
  cp -rf * ${pkgdir}/opt/${pkgname}
  cd ${pkgdir}/opt/${pkgname}
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
  ${pkgdir}/opt/${pkgname}/flexipatch-finalizer.sh -o "${pkgdir}/opt/${pkgname}" -d "${pkgdir}/opt/${pkgname}" -r --debug
  make PREFIX=/usr/local DESTDIR="${pkgdir}" install
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/st/LICENSE"
  install -Dm644 README "${pkgdir}/usr/share/doc/st/README"
}

