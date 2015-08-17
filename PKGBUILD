# Contributor: zoulnix <http://goo.gl/HQaP>


pkgname=tibia-game
pkgver=931
pkgrel=1
pkgdesc="A free 2D online role playing game."
arch=('i686' 'x86_64')
url="http://www.tibia.com/"
license=('custom:"CipSoft"')
[ "$CARCH" = "i686" ] && depends=('libxdamage' 'mesa')
[ "$CARCH" = "x86_64" ] && depends=('lib32-libxdamage' 'lib32-mesa')
makedepends=('')
source=(http://download.tibia.com/tibia${pkgver}.tgz \
	${pkgname}.desktop \
	${pkgname}.png \
	${pkgname}.sh)
md5sums=('265e185b9de71d7444a906517a711de5' 'e5c65792d3a30f8d005a50a1481cd0fe' \
	 '8aece042ac8ef9eca96c9fe95136817b' '6fed44754e5b51d40b98e92899ed346f')

build() {
  cd ${srcdir}/Tibia

}

package() {
  cd ${srcdir}/Tibia
  install -d ${pkgdir}/usr/share/{applications,pixmaps,${pkgname}} \
	     ${pkgdir}/usr/bin || return 1

  rm -rf ${srcdir}/Tibia/{libc6,*.sh}

  if [ "$CARCH" = "x86_64" ]; then
    install -d ${pkgdir}/usr/share/${pkgname}/libc6 || return 1
    ln -s /usr/lib32/ld-* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libanl* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libBrokenLocale* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libc-*,libc.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libcidn* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libcrypt* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libdl-*,libdl.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libm-*,libm.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libmemusage* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libnsl-*,libnsl.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libnss_* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libpcprofile* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libpthread* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libresolv* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{librt-*,librt.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libSegFault ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libthread_db* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libutil-*,libutil.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1

    ln -s /usr/lib32/libXdamage* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
  fi

  install -m755 ${startdir}/${pkgname}.sh ${pkgdir}/usr/bin/${pkgname} || return 1
  install -m755 Tibia ${pkgdir}/usr/share/${pkgname}/ || return 1
  install -m644 {*.dat,*.pic,*.spr,Patch,Showerror} ${pkgdir}/usr/share/${pkgname}/ || return 1

  install -m644 ${startdir}/${pkgname}.desktop ${pkgdir}/usr/share/applications/ || return 1
  install -m644 ${startdir}/${pkgname}.png ${pkgdir}/usr/share/pixmaps/ || return 1
  install -m644 Tibia.xpm ${pkgdir}/usr/share/pixmaps/${pkgname}.xpm || return 1
}
