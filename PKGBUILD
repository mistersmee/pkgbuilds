# Maintainer: Aseem Athale <athaleaseem@gmail.com>
_base=python-crfsuite
pkgname=${_base}-git
pkgver=0.99.r1.g84e9a76
pkgrel=1
pkgdesc="A Python implementation of the Metaphone and Double Metaphone algorithms"
arch=('any')
url="https://github.com/scrapinghub/${_base}"
license=('custom:BSD-3-clause')
depends=('python')
makedepends=('python-build' 'python-wheel' 'python-installer' 'python-setuptools' 'python-tox' 'cython' 'git')
# options=(!emptydirs)
source=("git+https://github.com/scrapinghub/python-crfsuite.git"
        "git+https://github.com/chokkan/crfsuite.git"
        "git+https://github.com/chokkan/liblbfgs.git")
sha512sums=("SKIP"
            "SKIP"
            "SKIP")

pkgver() {
  cd "${_base}"
  git describe --long --tags --abbrev=7 | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd "${_base}"
  cython pycrfsuite/_pycrfsuite.pyx --cplus -a -2 -I pycrfsuite

  git submodule init

  git config submodule.crfsuite/crfsuite.url "$srcdir/crfsuite"
  git config submodule.liblbfgs/liblbfgs.url "$srcdir/liblbfgs"

  git -c protocol.file.allow=always submodule update
}

build() {
  cd "${_base}"
  python -m build --wheel --no-isolation
}

package() {
  cd "${_base}"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm 644 LICENSE.txt -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
