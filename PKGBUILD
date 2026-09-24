pkgname=goodaccess
pkgver=4.7.2
_debrel=1
pkgrel=1
pkgdesc="Zero-trust network access and VPN client (repackaged from the official .deb)"
arch=('x86_64')
url="https://www.goodaccess.com"
license=('custom')
depends=(
  'glibc'
  'gcc-libs'
  'gtk3'
  'nss'
  'alsa-lib'
  'libcups'
  'mesa'
  'libxkbcommon'
  'at-spi2-core'
  'systemd'
  'iputils'
  'dmidecode'
  'bash'
)
options=('!strip' '!debug')
install=goodaccess.install
source=("https://goodaccess-storage.b-cdn.net/applications/prod/linux/repos/deb/pool/main/${pkgname}_${pkgver}-${_debrel}_amd64.deb")
noextract=("${pkgname}_${pkgver}-${_debrel}_amd64.deb")
sha256sums=('2761e4923eb697c181bc29151c137f722846f1982b413adae7aeef21dffd69a2')

package() {
  bsdtar -xOf "${pkgname}_${pkgver}-${_debrel}_amd64.deb" 'data.tar.*' | bsdtar -xpf - -C "$pkgdir"

  install -dm755 "$pkgdir/usr/lib"
  mv "$pkgdir/lib/systemd" "$pkgdir/usr/lib/"
  rmdir "$pkgdir/lib"

  rm -rf "$pkgdir/usr/share/doc"
  rmdir "$pkgdir/etc/xdg"
}
