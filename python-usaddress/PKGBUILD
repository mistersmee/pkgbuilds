# Maintainer: Aseem Athale <athaleaseem@gmail.com>

_base=usaddress
pkgname=python-${_base}
pkgver=0.5.10
pkgrel=1
pkgdesc="A python library for parsing unstructured United States address strings into address components."
arch=('any')
url="https://github.com/datamade/${_base}"
license=(MIT)
depends=('python' 'python-crfsuite' 'python-future' 'python-probableparsing')
makedepends=('python-setuptools' 'python-build' 'python-installer' 'python-wheel')
source=("$pkgname-$pkgver.tar.gz"::${url}/archive/refs/tags/v${pkgver}.tar.gz)
sha512sums=('437a10bc3aad949c9d585baa544e57a404bd40b90944c89d56dc735870933e5e37bbf8298d307cf0b587a60c6eb3e811a36c34b661d0190c456d4746d350f53f')

build() {
  cd "${_base}-${pkgver}"
  python -m build --wheel --no-isolation
}

package() {
  cd "${_base}-${pkgver}"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm 644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
