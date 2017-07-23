pkgname=archrepo-git
pkgver=6.3d74282
pkgrel=1
pkgdesc='Archlinux Personal Repository Tools'
arch=('any')
url='https://github.com/sidaf/archrepo'
license=('GPL2')
makedepends=('git')
depends=('bash' 'devtools' 'hardlink')

pkgver() {
  cd "$startdir"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

package() {
  cd "$startdir"
  install -dm755 "$pkgdir"/usr/{share/licenses/$pkgname,share/devtools,bin}
  # install legal stuff
  install -m644 COPYRIGHT LICENSE "$pkgdir/usr/share/licenses/$pkgname"
  # install config
  install -m644 pacman-ppa.conf "$pkgdir/usr/share/devtools"
  install -m644 pacman-multilib-ppa.conf "$pkgdir/usr/share/devtools"
  # install binaries
  install -m755 ppa-build ppa-build-all ppa-build-commit ppa-mirrors ppa-commit \
    ppa-remove ppa-cleanup ppa-list ppa-push rebuild-arch-chroots update-arch-chroots \
    "$pkgdir/usr/bin"
  # symlink archbuild
  ln -s archbuild "$pkgdir/usr/bin/ppa-i686-build"
  ln -s archbuild "$pkgdir/usr/bin/ppa-x86_64-build"
  ln -s archbuild "$pkgdir/usr/bin/multilib-ppa-build"
}

# vim:set ts=2 sw=2 et:
