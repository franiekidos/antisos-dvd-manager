pkgname=antisos-dvd-manager
pkgver=1.0.0
pkgrel=1
pkgdesc="AntisOS DVD Managing Software"
arch=('x86_64')
url="https://example.com/project-homepage"
license=('GPL')
# Use 'depends' for dependencies required at runtime
depends=(gtk4 python-vlc)
# Use 'makedepends' for dependencies only needed to build the package (e.g., git, cmake, g++)
makedepends=(pyinstaller)
# List the source files, usually a tarball URL or a git repository
source=("git+https://github.com/franiekidos/antisos-dvd-manager.git")
# Optional: Add integrity checks for the source file
sha256sums=(SKIP)

build() {
    cd $srcdir/antisos-dvd-manager
    pyinstaller \
    --onefile \
    --name "antisos-dvd-manager" \
    --clean \
    --noconsole \
    "antisos-dvd-manager"

    BUILD_STATUS=$?
    if [ $BUILD_STATUS -ne 0 ]; then
        echo ":: ERROR: PyInstaller failed to create the executable."
        exit 1
    fi
}

package() {
   install -Dm755 $srcdir/antisos-dvd-manager/dist/antisos-dvd-manager ${pkgdir}/usr/bin/antisos-dvd-manager
   install -Dm755 $srcdir/antisos-dvd-manager/antisos-dvd-manager.desktop ${pkgdir}/usr/share/applications/antisos-dvd-manager.desktop
}