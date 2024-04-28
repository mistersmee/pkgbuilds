# Maintainer: Aseem Athale <athaleaseem@gmail.com>

_base=parserator
pkgname=python-${_base}
pkgver=0.6.8
pkgrel=1
pkgdesc="A toolkit for making domain-specific probabilistic parsers"
arch=('any')
url="https://github.com/datamade/${_base}"
license=(MIT)
depends=('python' 'python-future' 'python-lxml' 'python-crfsuite' 'python-chardet')
makedepends=('python-setuptools' 'python-build' 'python-installer' 'python-wheel')
source=("$pkgname-$pkgver.tar.gz"::${url}/archive/refs/tags/v${pkgver}.tar.gz)
sha512sums=('2edc8c0309d9f5ac2b9570c606f7bb4ec1845ab09dc2eac371e10ebf0a21b167d687e76faa81c8e800f394345573e072a0db398c0abf4ba83023e73d9867a059')

build() {
  cd "${_base}-${pkgver}"
  python -m build --wheel --no-isolation
}

package() {
  cd "${_base}-${pkgver}"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm 644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
