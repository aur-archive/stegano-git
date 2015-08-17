#Contributor: Simone Solinas ksolsim <ksolsim@gmail.com>

pkgname=stegano-git
pkgver=20130623
pkgrel=4
pkgdesc='A steganography tool for KDE Plasma workspaces.'
arch=('i686' 'x86_64')
url='https://github.com/sassman/stegano.kde4'
license=('GPL2')
depends=('kdelibs' 'quazip' 'qca')
makedepends=('cmake' 'git' 'automoc4')

_gitroot="git://anongit.kde.org/scratch/assmann/stegano.kde"
_gitname="stegano.kde"

build() {

cd $srcdir
  msg "Connecting to the GIT server...."
  
  if [[ -d $srcdir/$_gitname ]] ; then
    cd $_gitname
    git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi
  
  msg "GIT checkout done"
  msg "Starting make..."
  if [[ -d ${srcdir}/${_gitname}-build ]]; then
    rm -rf ${srcdir}/${_gitname}-build
  fi

  mkdir $srcdir/$_gitname-build
 
  cd $srcdir/$_gitname-build

  cmake $startdir/src/$_gitname -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd ${srcdir}/$_gitname-build
  make DESTDIR=${pkgdir} install
}
