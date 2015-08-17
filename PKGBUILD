# Contributor: OS Hazard  <oshazard+aur@gmail.com>
pkgname=qlprism-bin
_pkgname=qlprism
pkgver=4.40
pkgrel=1
pkgdesc="Light-weight Quake Live stand-alone launcher based on Mozilla Lab's Prism"
arch=("i686" "x86_64")
url="http://www.qlprism.us"
_arch=$(uname -m)
DLAGENTS=('http::/usr/bin/curl -A firefox -fLC - --retry 3 --retry-delay 3 -o %o %u') 
source=(http://download.qlprism.us/qlprism-$pkgver-linux-x86_64.tar.gz http://aur-includes.googlecode.com/git/qlprism-bin/includes.tar.gz)
md5sums=('a77a2223ca348794395f9e4fe8d25449' '0f974a22dee11281a1e95425d5373e41')
depends=('libxxf86dga' 'lib32-gtk2' 'lib32-libxt' 'lib32-pcre')
install=qlprism.install
license=("custom")
conflicts=('qlprism')
provides=('qlprism')

if [ ${_arch} = "x86_64" ]; then
  source=(http://download.qlprism.us/qlprism-$pkgver-linux-x86_64.tar.gz http://aur-includes.googlecode.com/git/qlprism-bin/includes.tar.gz)
  md5sums=('a77a2223ca348794395f9e4fe8d25449' '0f974a22dee11281a1e95425d5373e41')
  depends=('libxxf86dga' 'lib32-gtk2' 'lib32-libxt' 'lib32-pcre')
elif [ ${_arch} = "i686" ]; then
  source=(http://download.qlprism.us/qlprism-$pkgver-linux-i686.tar.gz http://aur-includes.googlecode.com/git/qlprism-bin/includes.tar.gz)
  md5sums=('8c06780577628fab994534a5da01ff8f' '0f974a22dee11281a1e95425d5373e41')
  depends=('libxxf86dga' 'gtk2' 'libxt' 'pcre')
else
  unset source
fi

package () {
  cd $srcdir
  install -d "${pkgdir}/opt"
  cp -dpr --no-preserve=ownership "${_pkgname}-${CARCH}" "${pkgdir}/opt/${_pkgname}"
  chgrp -R wheel "${pkgdir}/opt/${_pkgname}"
  chmod -R 777 "${pkgdir}/opt/${_pkgname}"

  install -d "${pkgdir}/usr/bin"
  ln -s "/opt/${_pkgname}/${_pkgname}.sh" "${pkgdir}/usr/bin/${_pkgname}"

  install -Dm644 ${_pkgname}.png ${pkgdir}/usr/share/icons/hicolor/64x64/apps/${_pkgname}.png
  install -Dm644 ${_pkgname}.desktop ${pkgdir}/usr/share/applications/${_pkgname}.desktop
}

