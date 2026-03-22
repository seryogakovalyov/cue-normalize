pkgname=cue-normalize
pkgver=1.0.0
pkgrel=1
pkgdesc='Minimal Bash CLI to normalize and repair problematic CUE files'
arch=('any')
url='https://github.com/sergey/cue-normalize'
license=('MIT')
depends=('bash' 'coreutils' 'findutils' 'gawk' 'grep' 'perl' 'file' 'sed')
optdepends=('uchardet: better encoding detection')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/sergey/cue-normalize/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('SKIP')

package() {
  install -Dm755 "${srcdir}/${pkgname}-${pkgver}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
  install -Dm644 "${srcdir}/${pkgname}-${pkgver}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
