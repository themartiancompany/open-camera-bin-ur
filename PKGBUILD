# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_offline="false"
_git="false"
_pkgname="open-camera"
_pkg="net.sourceforge.${_pkgname/-/}"
_Pkg="OpenCamera"
pkgname="${_pkgname}-bin"
pkgver=1.53.1
# _commit="e117ccae32d5a7d75479b61f034000122fe9fa24"
pkgrel=90
_pkgdesc=(
  "A feature rich camera application."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
url="${_pkgname/-/}.org.uk"
license=(
  GPL3
)
depends=(
)
_os="$( \
  uname \
    -o)"
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  depends+=(
    inteppacman
  )
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=(
  coreutils
)
checkdepends=(
)
provides=(
  "${_pkgname}=${pkgver}"
)
conflicts=(
  "${_pkgname}"
)
source=()
sha256sums=()
_url="https://f-droid.org/repo"
_tag="${pkgrel}"
_tag_name="pkgrel"
_tarname="${_pkgname}-${pkgver}-${pkgrel}"
[[ "${_offline}" == "true" ]] && \
  _url="file://${HOME}/${pkgname}"
[[ "${_git}" == true ]] && \
  makedepends+=(
    "git"
  ) && \
  source+=(
    "${_tarname}::git+${_url}#${_tag_name}=${_tag}"
  ) && \
  sha256sums+=(
    SKIP
  )
[[ "${_git}" == false ]] && \
  if [[ "${_tag_name}" == 'pkgrel' ]]; then
    _tar="${_tarname}.apk::${_url}/${_pkg}_${pkgrel}.apk"
    _sig="${_tarname}.apk.sig::${_url}/${_pkg}_${pkgrel}.apk.asc"
    _sum="3b58721af4a79f42f5e6f6832a998493719b519f0d65d942d15a9593845049e4"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _tar="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="dacf4a05e8dab38c49034e5d58deb477c36d005fe81324cf7973ba5487d87eb7"
  fi && \
    source+=(
      "${_tar}"
      "${_sig}"
    ) && \
    sha256sums+=(
      "${_sum}"
      "SKIP"
    )
validgpgkeys=(
  # F-droid binary releases
  "37D2C98789D8311948394E3E41E7044E1DBA2E89"
)

package() {
  local \
    _dest_dir \
    _dest
  _dest_dir="/usr/bin"
  _dest="${_pkgname}.apk"
  if [[ "${_os}" == "Android" ]]; then
    _dest_dir="/system/app/${_Pkg}"
    _dest="base.apk"
  fi
  install \
    -dm755 \
    "${pkgdir}${_dest_dir}"
  install \
    -Dm644 \
    "${srcdir}/${_tarname}.apk" \
    "${pkgdir}/${_dest_dir}/${_dest}"
}

# vim: ft=sh syn=sh et
