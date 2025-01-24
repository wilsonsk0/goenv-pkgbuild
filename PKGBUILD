# Maintainer: Sam Wilson <swilson0702@gmail.com>

pkgname=goenv
pkgver=2.2.18
pkgrel=1
pkgdesc="Like pyenv and rbenv, but for Go."
arch=('any')
depends=('bash')
checkdepends=('git' 'make')
url="https://github.com/go-nv/goenv"
license=('MIT')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz")
md5sums=('789a9d83cb97d7cd2f22f748cd46d9bd')
install=goenv.install

check() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make test || true
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  install -d "${pkgdir}/usr/lib/goenv/"
  cp -r libexec "${pkgdir}/usr/lib/goenv/"
  cp -r plugins "${pkgdir}/usr/lib/goenv/"

  install -D -m644 APP_VERSION "${pkgdir}/usr/lib/goenv/"

  install -D -m644 completions/goenv.bash "${pkgdir}/usr/share/bash-completions/completions/goenv"
  install -D -m644 completions/goenv.zsh "${pkgdir}/usr/share/zsh/site-functions/_goenv"
  install -D -m644 completions/goenv.fish "${pkgdir}/usr/share/fish/vendor_completions.d/goenv.fish"

  license_files=(
    "LICENSE"
  )
  install -d "${pkgdir}/usr/share/licenses/goenv/"
  for file in "${license_files[@]}"; do
    install -D -m644 "$file" "${pkgdir}/usr/share/licenses/goenv/"
  done

  doc_files=(
    "ADVANCED_CONFIGURATION.md"
    "CHANGELOG.md"
    "COMMANDS.md"
    "CONTRIBUTING.md"
    "ENVIRONMENT_VARIABLES.md"
    "HOW_IT_WORKS.md"
    "README.md"
  )
  install -d "${pkgdir}/usr/share/doc/goenv/"
  for file in "${doc_files[@]}"; do
    install -D -m644 "$file" "${pkgdir}/usr/share/doc/goenv/"
  done
}

