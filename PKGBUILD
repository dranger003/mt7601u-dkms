pkgname=mt7601u-dkms
pkgver=v3.0.0.4
pkgrel=1
pkgdesc="Driver for Ralink MT7601U chipset wireless adaptors"
arch=('any')
url="http://www.mediatek.com/"
license=('GPL')
depends=('dkms')
conflicts=()
install=${pkgname}.install
options=(!strip)
_pkgname="mt7601u"
source=("http://mediatek.com/AmazonS3/Downloads/linux/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913.tar.bz2"
        "dkms.conf"
        "fix-279.patch")
md5sums=('5f440dccc8bc952745a191994fc34699'
         '761cc7f7f484486e080397e06b412d54'
         'b40da03b6623b73acf79d5355c9e8ced')

package() {
    mv ${srcdir}/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913 ${srcdir}/$_pkgname-$pkgver

    installDir="$pkgdir/usr/src/$_pkgname-$pkgver"

    install -dm755 "$installDir"
    install -m644 "$srcdir/dkms.conf" "$installDir"
    install -dm755 "$pkgdir/etc/modprobe.d"

    cd "${srcdir}/${_pkgname}-${pkgver}/"

    patch -p1 -i "$srcdir/fix-279.patch"

    for d in `find . -type d`
    do
        install -dm755 "$installDir/$d"
    done

    for f in `find . -type f`
    do
        install -m644 "${srcdir}/${_pkgname}-${pkgver}/$f" "$installDir/$f"
    done
}
