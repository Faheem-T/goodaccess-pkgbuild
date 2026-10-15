pkgname=goodaccess
pkgver=4.8.0
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
  'wireguard-tools'
  'iproute2'
  'iptables'
  'polkit'
)
options=('!strip' '!debug')
install=goodaccess.install
source=("https://goodaccess-storage.b-cdn.net/applications/prod/linux/repos/deb/pool/main/${pkgname}_${pkgver}-${_debrel}_amd64.deb")
noextract=("${pkgname}_${pkgver}-${_debrel}_amd64.deb")
sha256sums=('9ceb57611e2f4ebdcd7a13ced2dbeb6110d339996c26055494d48f9c79439364')

package() {
  bsdtar -xOf "${pkgname}_${pkgver}-${_debrel}_amd64.deb" 'data.tar.*' | bsdtar -xpf - -C "$pkgdir"

  install -dm755 "$pkgdir/usr/lib"
  mv "$pkgdir/lib/systemd" "$pkgdir/usr/lib/"
  rmdir "$pkgdir/lib"

  rm -rf "$pkgdir/usr/share/doc"
  rm -rf "$pkgdir/etc/xdg"
}
