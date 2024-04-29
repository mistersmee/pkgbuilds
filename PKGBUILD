# Maintainer: Aseem Athale <athaleaseem@gmail.com>

_name=varname
pkgname=python-varname
pkgver=0.13.0
pkgrel=3
pkgdesc="A Python library to retrieve variable names from functions or classes"
arch=('any')
url="https://github.com/pwwang/${pkgname}"
license=('MIT')
depends=('python')
makedepends=('python-setuptools' 'python-build' 'python-installer' 'python-wheel' 'python-poetry' 'python-virtualenv' 'python-cachecontrol' 'python-poetry-plugin-export' 'python-jsonschema')
source=(${url}/archive/refs/tags/${pkgver}.tar.gz)
sha512sums=('ab0703330f7c98f92032b0a98c770e4ef6c737c5788cc18674c0be8e4930b9e2441385f3478fe23f6db208fb58019d4a7efb2d740fb3e527b6ce5146a976d3d0')

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
