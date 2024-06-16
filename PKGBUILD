# Maintainer: mequam <blue9ja@gmail.com>

pkgname="botbertd"
pkgver=1.0.0
pkgrel=1
pkgdesc="botbert runtime for servers :)"
arch=('x86_64' 'aarch64')
url="https://github.com/Mequam/botbert"
license=('MIT')
depends=('python')
makedepends=('git' 'python-pip')
optdepends=()
_start_script="${pkgname}-${pkgver}-start.sh"
_commit=c9adf2f1985449e837906bcb7c5ae8039962fbd8
source=(
    "${pkgname}-${pkgver}::git+https://github.com/Mequam/botbert.git#commit=$_commit"
    $_start_script
)
sha256sums=('30faefdf41a056d155dec72da7c7fe467d1ab11a9d674197725b3ed6c3bff2b4'
            '3b403b11600f57bc9dffaf9e1e6fdff23ae9bc269c0ebe8e68b01fdc2c422553')
#prepare() {
#    #cd "${pkgname}-${pkgver}"
#    #git clone "${pkgname}-${pkgver}" ${srcdir}
#}

build() {
   cd "${pkgname}-${pkgver}"
   
   #set up the viratual environment necessary for the bot
   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
}
###
###check() {
###    cd "${pkgname}-${pkgver}"
###    export RUSTUP_TOOLCHAIN=stable
###    export CARGO_TARGET_DIR=target
###    cargo test --frozen
###}
###
package() {
    #install -Dm644 -t "${pkgdir}/usr/lib/systemd/system" "${pkgname}.service"
    mkdir -p "${pkgdir}/opt/botbertd"
    cp -r "${pkgname}-${pkgver}"/* "${pkgname}-${pkgver}"/.venv "${pkgdir}/opt/botbertd"
    install -Dm755 -t "${pkgdir}/usr/bin/botbertd" $_start_script

    #install -D -t "${pkgdir}/opt/botbertd" "${pkgname}-${pkgver}/"
    #install -Dm755 -t "${pkgdir}/usr/bin" "${pkgname}-${pkgver}/target/release/${pkgname}"
    #install -Dm644 -t "${pkgdir}/usr/share/licenses/${pkgname}" "${pkgname}-${pkgver}/LICENSE"
}

