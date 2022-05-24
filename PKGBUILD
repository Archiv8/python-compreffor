#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-comprefforpyclipper/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-compreffor/discussions>

_langname="python"
_relname="compreffor"

pkgname="${_langname}-${_relname}"
pkgver=0.5.1.post1
pkgrel=1
pkgdesc="A CFF table suroutinizer for FontTools"
arch=(
  "x86_64"
)
url="https://github.com/googlefonts/python-compreffor"
license=(
  "Apache"
)
depends=(
  "python"
  "python-fonttools"
)
makedepends=(
  "cython"
  "python-setuptools-git-ls-files"
  "python-setuptools-scm"
  "python-wheel"
)
checkdepends=(
  "python-pytest"
)
_tarname="${_relname}-${pkgver}"
source=(
	"https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_tarname}.tar.gz"
	)
sha512sums=(
	"eaab7e01b158f68c28c946f39af80bd8313b9338301aee8a4119de243442791d68cf7edc0e8ac86efc0cadf6115de89f38ec445cf5ce13055aed44dcfaeb3eed"
	)

build() {

  cd "${_tarname}"

  python setup.py build_ext --inplace

  python setup.py build
}

check() {

  cd "${_tarname}/src/python"

  PYTHONPATH=. pytest compreffor/test
}

package() {

  cd "${_tarname}"

  python setup.py install --root="$pkgdir" --optimize=1 --skip-build
}
