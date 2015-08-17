pkgname=pysoy-hg
pkgver=2489
pkgrel=1
pkgdesc='PySoy is a 3d cloud game engine for Python'
arch=('i686' 'x86_64')
url='http://www.pysoy.org/'
license=('GPL')
depends=('libsoy-hg' 'python3' 'python-sphinx' 'libgee')
makedepends=('mercurial' 'python3' 'gcc')

_hgroot='http://hg.pysoy.org/'
_hgrepo='pysoy'

build() {
  cd $srcdir

  # Update the repo, else clone a new one
  if [ -d $_hgrepo ]; then
    cd $_hgrepo
    ./waf clean
    hg pull -u
  else
    hg clone ${_hgroot}/${_hgrepo}
    cd $_hgrepo
  fi

  ./waf configure --prefix=$pkgdir/usr || return 1
  ./waf build || return 1
}

package() {
  cd $srcdir/"$_hgrepo"
  ./waf install --destdir=$pkgdir || return 1
}
