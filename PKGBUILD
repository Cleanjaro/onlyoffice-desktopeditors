# Maintainer:  David Spink <yorper_protonmail.com>
# Contributor: Josip Ponjavic <josipponjavic_gmail.com>

pkgname=onlyoffice-desktopeditors
pkgver=5.3.5
pkgrel=3
pkgdesc='Open-source office suite that combines text, spreadsheet and presentation editors.'
url="https://www.onlyoffice.com/"
license=('AGPL3')
arch=('x86_64')
provides=('onlyoffice' 'onlyoffice-bin')
conflicts=('onlyoffice' 'onlyoffice-bin')
depends=('desktop-file-utils' 'gconf' 'hicolor-icon-theme' 'ttf-dejavu' 'ttf-liberation' 'ttf-carlito')
options=(!strip !zipman)
source=("https://github.com/ONLYOFFICE/DesktopEditors/releases/download/ONLYOFFICE-DesktopEditors-${pkgver}/${pkgname}-x64.tar.gz"
        "${pkgname}.desktop"
        "onlyoffice-desktopeditors")
noextract=("${pkgname}-x64.tar.gz")
sha256sums=('e81df64843274e707ba61ca064694a087b9eceff5b4c24f19533121965913d88'
            '29920acdeff895763893275c543d4f568ed1a7ca1e8b493188636df708e69e9f'
            '29d03e3c729b6ff3be9e873eca228406f647960da59fd3ddfa4b22628192103d')

package() {
  install -d -m0755 "$pkgdir"/{usr/bin/onlyoffice,usr/bin}
  tar -zxvf ${pkgname}-x64.tar.gz -C "$pkgdir"/usr/bin/onlyoffice
  # suid sandbox
  chmod 4755 "$pkgdir/usr/bin/onlyoffice/desktopeditors/chrome-sandbox"
  
  install -D -m0755 "${srcdir}/onlyoffice-desktopeditors" "$pkgdir/usr/bin/onlyoffice-desktopeditors"
  install -Dm644 "${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  install -Dm644 "${pkgdir}/usr/bin/onlyoffice/desktopeditors/LICENSE.htm" $pkgdir/usr/share/licenses/$pkgname/LICENSE
  install -Dm644 "${pkgdir}/usr/bin/onlyoffice/desktopeditors/3DPARTYLICENSE" $pkgdir/usr/share/licenses/$pkgname/3DPARTYLICENSE
}
