pkgname=klnagent64
pkgver=11.2.0.4528
_pkgver_agent=12.0.0-60
pkgrel=1
pkgdesc="The Kaspersky Network Agent for KESL (Kaspersky Endpoint Security for Linux)"
arch=('x86_64')
url="https://support.kaspersky.com/kes11linux"
license=('custom')
depends=('perl')
install=$pkgname.install
source=("https://products.s.kaspersky-labs.com/endpoints/keslinux10/${pkgver}/multilanguage-${pkgver}/3437313131397c44454c7c31/klnagent64_${_pkgver_agent}_amd64.deb"
        "${pkgname}.install"
        "${pkgname}.service")
noextract=("klnagent64_${_pkgver_agent}_amd64.deb")
sha256sums=('d7f21826cc5d78a9aab5f66ea88ee545defcad2ab90c0a515b5426047fef82bc'
            'd747b1745af07531df56d17433516f8ad4f1ba64b5d2245c689bce55d3c2452d'
            '1c2d9b172b320faa81072bb21b1cf971f3dedbfafaa541e1ad9856d080870f8b')

package() {
    VAROPTDIR=${pkgdir}/var/opt/kaspersky/klnagent
    OPTDIR=${pkgdir}/opt/kaspersky/klnagent64

    # uncompress base packages
    bsdtar -xf klnagent64_${_pkgver_agent}_amd64.deb
    bsdtar -xf data.tar.xz -C ${pkgdir}/

    # fix permissions
    chmod 711 ${pkgdir}/opt/kaspersky

    # install service
    [ ! -d "${pkgdir}/usr/lib/systemd/system" ] && mkdir -p "${pkgdir}/usr/lib/systemd/system"
    install -m644 "${pkgname}.service" ${pkgdir}/usr/lib/systemd/system

    # man page symlinks
    [ ! -d "${pkgdir}/usr/share/man/man1" ] && mkdir -p "${pkgdir}/usr/share/man/man1"
    for m in $(find ${OPTDIR}/share/man/man1 -maxdepth 1 -mindepth 1 -type f);do
        ln -s /opt/kaspersky/klnagent64/share/man/man1/${m/*\/} ${pkgdir}/usr/share/man/man1/${m/*\/}
    done

    # install licenses
    for lic in $(find ${OPTDIR}/share/license -maxdepth 1 -mindepth 1 -type f |grep license);do
        install -Dm644 ${lic} "$pkgdir/usr/share/licenses/$pkgname/${lic/*\/}"
    done
}
