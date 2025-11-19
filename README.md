[![Build Packages Repositories](https://github.com/kakwa/freecad-pkg/actions/workflows/repos.yml/badge.svg)](https://github.com/kakwa/freecad-pkg/actions/workflows/repos.yml)
[![NVD CVEs check](https://github.com/kakwa/freecad-pkg/actions/workflows/vulncheck.yml/badge.svg)](https://github.com/kakwa/freecad-pkg/actions/workflows/vulncheck.yml)

# freecad-pkg

The `.deb`/`.rpm` repositories are available at the following url: https://kakwa.github.io/freecad-pkg/

## Ubuntu/Debian

If you are using `Ubuntu`/`Debian`, here how to install the repository:

```shell
# If you are not root
export SUDO=sudo

# Get your OS version
. /etc/os-release
# Get the architecture
ARCH=$(dpkg --print-architecture)

# Add the GPG key
wget -qO - https://kakwa.github.io/freecad-pkg/GPG-KEY.pub | \
    ${SUDO} tee /etc/apt/keyrings/freecad-pkg.asc >/dev/null

# Add the repository
cat << EOF | ${SUDO} tee /etc/apt/sources.list.d/freecad-pkg.sources
Architectures: ${ARCH}
Components: main
X-Repolib-Name: freecad-pkg
Signed-By: /etc/apt/keyrings/freecad-pkg.asc
Suites: ${VERSION_CODENAME}
Types: deb
URIs: https://kakwa.github.io/freecad-pkg/deb.${VERSION_CODENAME}.${ARCH}/
EOF

# update
apt update

# install
apt install astocad
```

## Build

This project uses [Pakste](https://github.com/kakwa/pakste).

Check the [Pakste Documention](https://kakwa.github.io/pakste/) for more details.
