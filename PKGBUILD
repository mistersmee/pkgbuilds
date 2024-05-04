# Maintainer: Aseem Athale <athaleaseem@gmail.com>

_name=varname
pkgname=python-varname
pkgver=0.13.1
pkgrel=1
pkgdesc="A Python library to retrieve variable names from functions or classes"
arch=('any')
url="https://github.com/pwwang/${pkgname}"
license=('MIT')
depends=('python' 'python-executing')
optdepends=('python-asttokens' 'python-pure-eval')
makedepends=('python-setuptools' 'python-build' 'python-installer' 'python-wheel' 'python-poetry')
source=(${url}/archive/refs/tags/${pkgver}.tar.gz)
sha512sums=('78808e298f32e7a5be8116865b60774b891fa7b921926fd186974bb48ecc7f23b1bbefb4199b97d9a17c035dc60729cb3fb3447587b0b6171831ef064eb6d597')

build() {
  cd "${pkgname}-${pkgver}"
	## skip dependency check because of pinned deps
  python -m build --wheel --no-isolation --skip-dependency-check
}

package() {
  cd "${pkgname}-${pkgver}"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm 644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
