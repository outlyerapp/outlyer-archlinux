# Maintainer: Tom Ashley <tom.ashley[at]outlyer[dot]com>
pkgname=outlyer-agent
pkgver=1.4.6
pkgrel=1
pkgdesc="The Full stack Outlyer Agent"
url="https://www.outlyer.com"
arch=('x86_64')
license=('GPL3')
depends=()
optdepends=()
makedepends=()
conflicts=()
replaces=()
backup=('etc/outlyer/agent.yaml')
install='outlyer-agent.install'
# https://s3.amazonaws.com/packages.outlyer.com/debian/pool/main/o/outlyer-agent/outlyer-agent_1.4.2-1_amd64.deb
source=("https://packages.outlyer.com/debian/pool/main/o/outlyer-agent/${pkgname}_${pkgver}-${pkgrel}_amd64.deb")
sha512sums=('70d363b3a276e68e5729a9e53acdd7fff8d8d9c247715babe56d4f6806e01ad9bc935f62820f44cfbbe9cb508bcda1a782d843553397986b9d249e463524a8d7')

package() {
  tar -xf data.tar.gz -C "$pkgdir/"

  # get rid of the SysV
  rm -rf "$pkgdir/etc/init"
  rm -rf "$pkgdir/etc/logrotate.d"
  rm -rf "$pkgdir/var"

  # install systemd unit file
  cp "$pkgdir"/lib/systemd/system/outlyer-agent.service .
  rm -rf "$pkgdir/lib"
  install -Dm644 outlyer-agent.service "$pkgdir"/usr/lib/systemd/system/outlyer-agent.service

}

# vim:set ts=2 sw=2 et:
