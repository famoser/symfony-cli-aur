# Maintainer: Florian Moser <arch@famoser.ch>

pkgname=symfony-cli
pkgrel=6
pkgver=5.8.15
pkgdesc="The Symfony client helps developers create and manage Symfony applications."
url="https://symfony.com/"
arch=('x86_64')
license=('AGPL3')
install="symfony-cli.install"
depends=('glibc')
makedepends=('git' 'go')
provides=('symfony-cli')
conflicts=('symfony-cli')
source=(
    "git+https://github.com/symfony-cli/symfony-cli#tag=v${pkgver}"
)
sha256sums=('6bd0312d8f73f1bbecadda7bd115284e21507140dbb109aa3ea7a7ba4b6539be')

build() {
  cd "symfony-cli"

  DATE=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
  PKGVER=${pkgver}

  go mod download
  go build -o symfony -trimpath -ldflags '-s -w -X main.channel=stable -X main.buildDate='"${DATE}"' -X main.version='"${PKGVER}"''
}

package() {    
    install -D -m 755 "${srcdir}/symfony-cli/symfony" "${pkgdir}/usr/bin/symfony"
}
