# Maintainer: Bernd Amend <bernd.amend(at)gmail(dot)com>
# Contributor: Alex Avance <aravance(at)gmail(dot)com>
# Contributor: Shen-Ta Hsieh <ibmibmibm(at)gmail(dot)com>

_pkgname=r8125
pkgname=${_pkgname}-dkms
pkgver=9.011.00
pkgrel=2
url="https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software"
pkgdesc="Kernel module for RTL8125"
license=('GPL2')
arch=('any')
depends=('dkms')
conflicts=("${_pkgname}")
optdepends=('linux-headers: Build the module for Arch kernel'
            'linux-lts-headers: Build the module for LTS Arch kernel')
source=("http://rtitwww.realtek.com/rtdrivers/cn/nic1/${_pkgname}-${pkgver}.tar.bz2" 'dkms.conf' 'aspm_rx_tx.patch' 'throughput.patch')
sha256sums=('01fbdb249b7ba2984df93a4bd11aecddd1ed904c6be10fc5d776e94b3110b2bf'
            'ad4c67e0c74661d19b74872f98254184d4b04e32e4c57b338a84fbcefa4c721f'
            '22c992e6a38176c5cd1912dd98a48a11c1359dcea4e642c7f70a832f8c5cfd7b'
            '92f19d6d95ce651946bf520f09e3354b9258ddf61de45b89165f946f9811173d')

prepare() {
  patch -Np0 <throughput.patch
  patch -Np0 <aspm_rx_tx.patch
}

package() {
  dir_name="${_pkgname}-${pkgver}"
  install -d "${pkgdir}"/usr/src/${dir_name}/
  install -Dm644 dkms.conf "${dir_name}"/src/* "${pkgdir}/usr/src/${dir_name}/"

  sed -e "s/@_PKGNAME@/${_pkgname}/g" \
      -e "s/@PKGVER@/${pkgver}/g" \
      -i "${pkgdir}/usr/src/${dir_name}/dkms.conf"
}
