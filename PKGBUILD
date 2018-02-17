# Maintainer: liberodark

pkgname=onlyoffice
pkgver=4.8.7
pkgrel=1
pkgdesc="The most complete and feature-rich office and productivity suite"
arch=('x86_64')
url="https://www.onlyoffice.com/"
license=('AGPL-3.0')
depends=('xdg-utils' 'alsa-lib' 'nss' 'libxtst' 'qt5-x11extras' 'qt5-svg' 'gconf' 'libx11' 'libxss' 'curl' 'gtkglext' 'cairo' 'libstdc++5' 'ttf-dejavu' 'ttf-liberation' 'libcurl-gnutls' 'libcurl-compat')
source_x86_64=("https://github.com/ONLYOFFICE/DesktopEditors/releases/download/ONLYOFFICE-DesktopEditors-${pkgver}-2/onlyoffice-desktopeditors_amd64.deb")
source=($pkgname.desktop
        $pkgname.png)
sha512sums=('b56f9888f18398d2fed8afc5555874971d292f5d84cd11185ae477d9b98aa4dc9558faeab8999b334b7b0449ea2b9c81ef608c86508f85b91f3050295cbe8f47'
         '560fb5dd677b273e1edf7be0d0ef066b44a83c538880896e7c2568da4fd3431db4c19ba9bec7f247800f9dc95a2f8b5543e81a1b0c475acdc12ef02ab5059e6f')
sha512sums_x86_64=('073338dc873ae452ad3bcb78b8e2a80a3e339b8221260c80c8fed051798368edf890bc43e270f2eccb5251438f35a4ce721ff2b4babbfc8b06682c01ac6e5c32')
        
package() {
  cd $srcdir
  tar xvf data.tar.xz
  cp -r usr $pkgdir
  cp -r opt $pkgdir
  rm $pkgdir/usr/share/applications/desktopeditors.desktop
  
  #fix wrong depedency
  ln -s "/usr/lib/libcurl-compat.so.4.5.0" "${pkgdir}/opt/onlyoffice/desktopeditors/converter/libcurl.so.4"
  #suid sandbox
  chmod 4755 "${pkgdir}/opt/onlyoffice/desktopeditors/chrome-sandbox"

  install -vDm644 $srcdir/$pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop
  install -vDm644 $srcdir/$pkgname.png $pkgdir/usr/share/pixmaps/$pkgname.png
}
