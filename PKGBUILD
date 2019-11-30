# Maintainer:  David Spink <yorper_protonmail.com>
# Contributor: Josip Ponjavic <josipponjavic_gmail.com>

pkgname=onlyoffice-desktopeditors
pkgver=5.4.2
pkgrel=1
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
sha256sums=('41a36c030746e05a4556af930b15419ac94aaf7ba3f0b95ec99aa0f339dd050f'
            '29920acdeff895763893275c543d4f568ed1a7ca1e8b493188636df708e69e9f'
            '8636c7806386c9e445808fb1ff68ddebf254971e927848eabd6e9b3e02b2de79')

package() {
  install -d -m0755 "$pkgdir"/{opt/onlyoffice,usr/bin}
  tar -zxvf ${pkgname}-x64.tar.gz -C "$pkgdir"/opt/onlyoffice
  # suid sandbox
  chmod 4755 "$pkgdir/opt/onlyoffice/desktopeditors/chrome-sandbox"
  # install script, desktop and license files
  install -D -m0755 "${srcdir}/onlyoffice-desktopeditors" "$pkgdir/usr/bin/onlyoffice-desktopeditors"
  install -Dm644 "${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  install -Dm644 "${pkgdir}/opt/onlyoffice/desktopeditors/LICENSE.htm" $pkgdir/usr/share/licenses/$pkgname/LICENSE
  install -Dm644 "${pkgdir}/opt/onlyoffice/desktopeditors/3DPARTYLICENSE" $pkgdir/usr/share/licenses/$pkgname/3DPARTYLICENSE
}
