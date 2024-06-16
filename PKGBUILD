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


_start_script="${pkgname}-${pkgver}-start.sh"
_service_script="${pkgname}-${pkgver}.service"
_env_variable_placeholder="${pkgname}-${pkgver}-env.txt"
_commit=c9adf2f1985449e837906bcb7c5ae8039962fbd8


source=(
    "${pkgname}-${pkgver}::git+https://github.com/Mequam/botbert.git#commit=$_commit"
    $_start_script
    $_service_script
    $_env_variable_placeholder
)
sha256sums=(
            '30faefdf41a056d155dec72da7c7fe467d1ab11a9d674197725b3ed6c3bff2b4'
            '3b403b11600f57bc9dffaf9e1e6fdff23ae9bc269c0ebe8e68b01fdc2c422553'
            '6415662e4127b9bb39f2e9d4f3d5f1e02a850f296e530d056b52081c86bf6f46'
            '633987eb0fb484558fddc3484726eafcb36a428d3ab9ad60c600209e49a22bcc'
           )
build() {
   cd "${pkgname}-${pkgver}"
   
   #set up the viratual environment necessary for the bot
   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
}
package() {
    mkdir -p "${pkgdir}/opt/botbertd"
    cp -r "${pkgname}-${pkgver}"/* "${pkgname}-${pkgver}"/.venv "${pkgdir}/opt/botbertd"
    
    mkdir -p "${pkgdir}/usr/bin/"
    cp $_start_script "${pkgdir}/usr/bin/botbertd"
    chmod +x "${pkgdir}/usr/bin/botbertd"


    mkdir -p "${pkgdir}/etc/systemd/system"
    cp $_service_script "${pkgdir}/etc/systemd/system/${pkgname}.service"
    

    mkdir -p "${pkgdir}/etc/botbertd/"
    cp $_env_variable_placeholder "${pkgdir}/etc/botbertd/env.txt"
}

