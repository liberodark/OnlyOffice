# Maintainer: liberodark

pkgname=onlyoffice
pkgver=4.8.0
pkgrel=1
pkgdesc="The most complete and feature-rich office and productivity suite"
arch=('x86_64')
url="https://www.onlyoffice.com/"
license=('AGPL-3.0')
depends=('xdg-utils' 'alsa-lib' 'nss' 'libxtst' 'qt5-x11extras' 'qt5-svg' 'gconf' 'libx11' 'libxss' 'curl' 'gtkglext' 'cairo' 'libstdc++5' 'ttf-dejavu' 'ttf-liberation' 'libcurl-gnutls' 'libcurl-compat')
source_x86_64=("https://github.com/ONLYOFFICE/DesktopEditors/releases/download/ONLYOFFICE-DesktopEditors-${pkgver}/onlyoffice-desktopeditors_amd64.deb")
source=($pkgname.desktop
        $pkgname.png)
sha512sums=('b56f9888f18398d2fed8afc5555874971d292f5d84cd11185ae477d9b98aa4dc9558faeab8999b334b7b0449ea2b9c81ef608c86508f85b91f3050295cbe8f47'
         '560fb5dd677b273e1edf7be0d0ef066b44a83c538880896e7c2568da4fd3431db4c19ba9bec7f247800f9dc95a2f8b5543e81a1b0c475acdc12ef02ab5059e6f')
sha512sums_x86_64=('d9945d52a6fb70dd5033ca4ea23cbbb609013126312b2eaf64a987d5362473c3624a20ac30fa5a9242c0369955667f9633a2a545fb987e3e872da8a494d71f91')
        
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
