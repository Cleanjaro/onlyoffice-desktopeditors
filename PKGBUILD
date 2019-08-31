# Maintainer: David Spink <yorper_protonmail.com>

pkgname=onlyoffice-desktopeditors
pkgver=5.3.5
pkgrel=2
pkgdesc='Open-source office suite that combines text, spreadsheet and presentation editors.'
url="https://www.onlyoffice.com/"
license=('AGPL3')
arch=('x86_64')
depends=('desktop-file-utils' 'gconf' 'hicolor-icon-theme' 'ttf-dejavu' 'ttf-liberation' 'ttf-carlito')
options=(!strip !zipman)
source=("https://github.com/ONLYOFFICE/DesktopEditors/releases/download/ONLYOFFICE-DesktopEditors-${pkgver}/${pkgname}-x64.tar.gz"
        "${pkgname}.desktop"
        "${pkgname}.sh"
        "ONLYOFFICE-LICENSE")
noextract=("${pkgname}-x64.tar.gz")
sha256sums=('e81df64843274e707ba61ca064694a087b9eceff5b4c24f19533121965913d88'
            '23496f1cb2dee73c86c9c7b62ab03c6bd33411dc98b703df07744a7764dbe19a'
            'f066e1f8c68696ef06319b2c41aacd44de7f5711b4b1a4e5543e4b9c5f393d59'
            'f8ea274edbd7f9238dbe5ee2363aa10407ef5b197f119c7f5a3d4cbe0b50dae3')

package() {
  install -d -m0755 "$pkgdir"/{usr/bin/onlyoffice,usr/bin}
  tar -zxvf ${pkgname}-x64.tar.gz -C "$pkgdir"/usr/bin/onlyoffice
  # suid sandbox
  chmod 4755 "$pkgdir/usr/bin/onlyoffice/desktopeditors/chrome-sandbox"
  install -D -m0755 "${srcdir}/${pkgname}.sh" $pkgdir/usr/bin/onlyoffice/desktopeditors/${pkgname}.sh
  install -Dm644 "${srcdir}/ONLYOFFICE-LICENSE" $pkgdir/usr/share/licenses/${pkgname}/ONLYOFFICE-LICENSE
  ln -s "/usr/bin/onlyoffice/desktopeditors/${pkgname}.sh" "${pkgdir}/usr/bin/${pkgname}"
  install -Dm644 "${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  install -Dm644 "${pkgdir}/usr/bin/onlyoffice/desktopeditors/LICENSE.htm" $pkgdir/usr/share/licenses/$pkgname/LICENSE
  install -Dm644 "${pkgdir}/usr/bin/onlyoffice/desktopeditors/3DPARTYLICENSE" $pkgdir/usr/share/licenses/$pkgname/3DPARTYLICENSE
}
