pkgname=spirv-headers
pkgver=1.4.328.1
pkgrel=3
pkgdesc="SPIR-V Headers"
arch=('x86_64')
url="https://www.khronos.org/registry/spir-v/"
license=('MIT')
groups=('vulkan-devel')
makedepends=(
    'cmake'
    'git'
    'ninja'
)
source=(git+ssh://git@github.com/KhronosGroup/SPIRV-Headers#tag=vulkan-sdk-${pkgver})
sha256sums=(8d4d0e7c1e60914372fb7dae6e491f346af481f73901fd4b0970be7f7ef73b81)

build() {
    cd SPIRV-Headers

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D CMAKE_INSTALL_LIBDIR=lib64
        -D CMAKE_INSTALL_SYSCONFDIR=/etc
        -D CMAKE_SKIP_INSTALL_RPATH=ON
    )

    cmake "${cmake_args[@]}"

    ninja -C flarebird-build
}

package() {
    cd SPIRV-Headers

    DESTDIR=${pkgdir} ninja -C flarebird-build install
}
