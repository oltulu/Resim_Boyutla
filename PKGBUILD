pkgname=resim-boyutla
pkgver=0.1
pkgrel=1
pkgdesc="Resim boyutlandırma programı"
arch=('i686' 'x86_64')
license=('GPL')
depends=('qt5-base')
makedepends=('git' 'qt5-base')

url='https://github.com/oltulu/Resim_Boyutla'

source=("${pkgname}::git+https://github.com/oltulu/Resim_Boyutla.git")
md5sums=('SKIP')

prepare() {
    cd ${srcdir}/${pkgname}
}

build() {
cd ${srcdir}/${pkgname}
qmake-qt5 Res-Boy.pro -spec linux-g++ CONFIG+=debug CONFIG+=qml_debug 
make
}

package(){
    cd ${srcdir}/${pkgname}
    make DESTDIR="$pkgdir/" install
    

# Başlatıcı 
mkdir -pv $pkgdir/usr/share/applications &&
cat > $pkgdir/usr/share/applications/$pkgname.desktop << "EOF" &&
#!/usr/bin/env xdg-open
[Desktop Entry]
Exec=Res-Boy
Icon=/usr/share/icons/res-boy.png
Name=Resim Boyutla
StartupNotify=true
Comment=Resim boyutlandırma programı
Terminal=false
Type=Application
Categories=Graphics;
EOF

    mkdir -pv $pkgdir/usr/bin
    mv Res-Boy $pkgdir/usr/bin/
    mkdir -pv $pkgdir/usr/share/icons
    mv res-boy.png $pkgdir/usr/share/icons/
}
