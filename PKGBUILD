# Maintainer: Tad Fisher <tadfisher at gmail dot com>

pkgname=('java8-icedtea')
pkgver=3.1.0
pkgrel=1
pkgdesc="A harness to build OpenJDK using Free Software build tools and dependencies"
arch=('i686' 'x86_64')
url='http://icedtea.classpath.org'
license=('custom')

makedepends=(
    'alsa-lib'
    'cups'
    'libxau'
    'libxdmcp'
    'libxinerama'
    'inputproto'
    'xextproto'
    'xineramaproto'
    'xproto'
    'cpio'
    'unzip'
    'zip'
    'ca-certificates'
    'openssl'
    'attr'
    'lsb-release'
    'libxt'
    'java-runtime'
    'paxctl'                    # AUR
)

optdepends=(
    'alsa-lib: sound support'
    'cups: printing support'
    'gtk2: GTK toolkit support'
)

depends=(
    'giflib'
    'libpng'
    'libx11'
    'libxext'
    'libxi'
    'libxrender'
    'libxtst'
    'libxcomposite'
    'glib2'
    'systemtap'                 # AUR
    'fontconfig'
    'lcms2'
    'zlib'
    'libjpeg'
    'freetype2'
    'lksctp-tools'              # optional?
    'pcsclite'                  # optional?
    'nss'                       # optional?
)

provides=()                     # TODO

_icedtea_pkg=icedtea-${pkgver}

_openjdk_tarball="openjdk.tar.xz"
_corba_tarball="corba.tar.xz"
_jaxp_tarball="jaxp.tar.xz"
_jaxws_tarball="jaxws.tar.xz"
_jdk_tarball="jdk.tar.xz"
_hotspot_tarball="hotspot.tar.xz"
_nashorn_tarball="nashorn.tar.xz"
_langtools_tarball="langtools.tar.xz"

_java_ver=8
_src_pkg="${_icedtea_pkg}.tar.xz"
_drop_url="http://icedtea.classpath.org/download/drops"
_icedtea_url="${_drop_url}/icedtea${_java_ver}/${pkgver}"
source=(
    "http://icedtea.classpath.org/download/source/${_src_pkg}"
    "${_icedtea_url}/${_openjdk_tarball}"
    "${_icedtea_url}/${_corba_tarball}"
    "${_icedtea_url}/${_jaxp_tarball}"
    "${_icedtea_url}/${_jaxws_tarball}"
    "${_icedtea_url}/${_jdk_tarball}"
    "${_icedtea_url}/${_hotspot_tarball}"
    "${_icedtea_url}/${_nashorn_tarball}"
    "${_icedtea_url}/${_langtools_tarball}"
)
noextract=(
    "${_openjdk_tarball}"
    "${_corba_tarball}"
    "${_jaxp_tarball}"
    "${_jaxws_tarball}"
    "${_jdk_tarball}"
    "${_hotspot_tarball}"
    "${_nashorn_tarball}"
    "${_langtools_tarball}"
)
sha256sums=('75616641ad6d8437124c32fed3fadddac67b14bba26757e15f6c2f69149233b4'
            'c19f7ffaec510db20b3c66b6447040012c28df319ab1dcfaf0a41c0e807bdddc'
            '5e334d4250de441517c0e761a3202dfdf4beacb75c0f7a03617b62d89cb71c21'
            '6d58edfd2b7f07b4d543910f7525fe08d94d56899b96493efce217b4a226aca3'
            '811ad76dfcffe1e6f2ef39a088f27a8858ed3371ef93816c8dc453f90516c7d7'
            '83880a4b865e33e7913bec603da1e5439ea3602b3540d8071408de7bef8162a9'
            '33581ea3ef4deffa786be82e110ae3d6b0431cc56140eb51453af1f11962b174'
            '56b36f5f7c073b140f8316084a23080553d8790d9f1f7e6d6288c6b0fd45cd7f'
            '2a7f8dd0b0c1b256c58b8e841033b7915beb08d983350f9a9357115a05677f1d')

_jvmdir=/usr/lib/jvm/java-8-icedtea
_prefix=out

check() {
    # TODO verify openjdk is active
    /bin/true
}

prepare() {
    cd "${srcdir}"
}

build() {
    unset JAVA_HOME JDK_HOME CLASSPATH JAVAC JAVACFLAGS

    cd "${srcdir}/${_icedtea_pkg}"
    sh configure \
       --with-openjdk-src-zip="../${_openjdk_tarball}" \
       --with-corba-src-zip="../${_corba_tarball}" \
       --with-jaxp-src-zip="../${_jaxp_tarball}" \
       --with-jaxws-src-zip="../${_jaxws_tarball}" \
       --with-jdk-src-zip="../${_jdk_tarball}" \
       --with-hotspot-src-zip="../${_hotspot_tarball}" \
       --with-nashorn-src-zip="../${_nashorn_tarball}" \
       --with-langtools-src-zip="../${_langtools_tarball}" \
       --with-jdk-home="/usr/lib/jvm/default" \
       --prefix="${pkgdir}/usr/lib/jvm/${_jvmdir}}" \
       --mandir="${pkgdir}/usr/share/man" \
       --docdir="${pkgdir}/usr/share/${pkgbase}" \
       --htmldir="${pkgdir}/usr/share/${pkgbase}/html" \
       --with-pkgversion="Arch ${pkgbase} ${pkgver}" \
       --disable-bootstrap \
       --disable-downloading --disable-tests \
       --enable-system-lcms --enable-system-jpeg \
       --enable-system-zlib --disable-systemtap-tests

    make
}

package() {
    # TODO
    /bin/true
}
