pkgname=spirv-headers
pkgver=1.4.321.0+54ae32b
pkgrel=2
pkgdesc="SPIR-V Headers"
arch=('x86_64')
url="https://www.khronos.org/registry/spir-v/"
license=('MIT')
groups=('vulkan-devel')
makedepends=(
    'cmake'
    'ninja'
)
source=(https://github.com/KhronosGroup/SPIRV-Headers/archive/vulkan-sdk-${pkgver%+*}/SPIRV-Headers-vulkan-sdk-${pkgver%+*}.tar.gz
    https://github.com/KhronosGroup/SPIRV-Headers/compare/2a611a970fdbc41ac2e3e328802aed9985352dca...54ae32bce772b29a253b18583b86ab813ed1887c.patch)
sha256sums=(5bbea925663d4cd2bab23efad53874f2718248a73dcaf9dd21dff8cb48e602fc
    f1d26ed3177c56d81245104e1eb000409e80604eaa8db9be5980ce58807795f0)

prepare() {
    cd SPIRV-Headers-vulkan-sdk-${pkgver%+*}

    patch -p1 -i ${srcdir}/2a611a970fdbc41ac2e3e328802aed9985352dca...54ae32bce772b29a253b18583b86ab813ed1887c.patch
}

build() {
    cd SPIRV-Headers-vulkan-sdk-${pkgver%+*}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D CMAKE_INSTALL_LIBDIR=lib64
        -D CMAKE_SKIP_INSTALL_RPATH=ON
    )

    cmake "${cmake_args[@]}"

    ninja -C flarebird-build
}

package() {
    cd SPIRV-Headers-vulkan-sdk-${pkgver%+*}

    DESTDIR=${pkgdir} ninja -C flarebird-build install
}
