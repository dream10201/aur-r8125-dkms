# Maintainer: Bernd Amend <bernd.amend(at)gmail(dot)com>
# Contributor: Alex Avance <aravance(at)gmail(dot)com>
# Contributor: Shen-Ta Hsieh <ibmibmibm(at)gmail(dot)com>

_pkgname=r8125
pkgname=${_pkgname}-dkms
pkgver=9.012.04
pkgrel=2
url="https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software"
pkgdesc="Kernel module for RTL8125"
license=('GPL2')
arch=('any')
depends=('dkms')
conflicts=("${_pkgname}")
optdepends=('linux-headers: Build the module for Arch kernel'
            'linux-lts-headers: Build the module for LTS Arch kernel')
source=("http://rtitwww.realtek.com/rtdrivers/cn/nic1/${_pkgname}-${pkgver}.tar.bz2" 'dkms.conf' 'optimal.patch')
sha256sums=('cb5e66c983b42cc32609464c32a2097b8301f09853020e11950d3fd5de0bb4e2'
            'ad4c67e0c74661d19b74872f98254184d4b04e32e4c57b338a84fbcefa4c721f'
            '22d80c25202e0161256efdddec16c6a6782ca5fe5c390ca72c082baa2cbac4e5')

prepare() {
  patch -Np0 < optimal.patch
}

package() {
  dir_name="${_pkgname}-${pkgver}"
  install -d "${pkgdir}"/usr/src/${dir_name}/
  install -Dm644 dkms.conf "${dir_name}"/src/* "${pkgdir}/usr/src/${dir_name}/"

  sed -e "s/@_PKGNAME@/${_pkgname}/g" \
      -e "s/@PKGVER@/${pkgver}/g" \
      -i "${pkgdir}/usr/src/${dir_name}/dkms.conf"
}
