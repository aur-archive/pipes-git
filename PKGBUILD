# Maintainer: Daniel Leining <daniel@the-beach.co> 
pkgname=pipes-git
pkgver=20121205
pkgrel=1
pkgdesc="pipes screensaver for terminal"
arch=(any)
url="https://github.com/0xAether/pipes"
license=('GPL')
groups=()
depends=('bc')
makedepends=('git')

_gitroot="git://github.com/0xAether/pipes.git"
_gitname="pipes"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"
}

package() {
  cd "$srcdir/$_gitname-build"
  install -D -m755 pipes.sh "$pkgdir/usr/bin/pipes"
}

# vim:set ts=2 sw=2 et:
