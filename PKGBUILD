# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=elb-instance-status
pkgver=1.0.0
pkgrel=1
pkgdesc="Small monitoring daemon for AWS Autoscaling Group Healthchecks"

arch=('i686' 'x86_64')
backup=("etc/${pkgname}.yml")
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
depends=()
makedepends=('go')
source=(
  "${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz"
  "elb-instance-status.yml"
)
sha512sums=(
  '92ec4ca9dd41375ac93a7f163b3a52af139d71fc711dffd1d073678c563da0a7336b93820c34f2844ed23d0cb76168b5a6ea8817a2ed8932c43902f397f05d46'
  'bbd6a0d6f0ba8bcb9bf05b200b231b1b4ab7f37a069414b7075634298931825c843a8b4ab136a360be3009554915d5748939d60ddc7585ea0223c26a1402e97a'
)

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  go build \
    -trimpath \
    -buildmode=pie \
    -ldflags="-X main.version=${pkgver}" \
    -mod=readonly \
    -modcacherw \
    -o ${pkgname}
}

package() {
  install -Dm644 -t "${pkgdir}/etc" "${srcdir}/${pkgname}-${pkgver}/${pkgname}.yml"
  install -Dm755 -t "${pkgdir}/usr/bin" "${srcdir}/${pkgname}-${pkgver}/${pkgname}"
  install -Dm644 -t "${pkgdir}/usr/share/licenses/${pkgname}" "${srcdir}/${pkgname}-${pkgver}/LICENSE"
}
