# Maintainer: Tom Ashley <tom.ashley[at]outlyer[dot]com>
pkgname=outlyer-agent
pkgver=1.4.2
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
sha512sums=('eca508a5840e7442d67f2a57e9e5ae39c34989c9852d83e2aa54bd939263106b8eff23c5a7fd89fa068ac618a1d65db3110099528ec9c58e15d3f5a0f7d2cc13')

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
