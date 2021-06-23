FROM dasbaumwolltier/archlinuxarm:aarch64

RUN pacman -Suy --noconfirm &&\
    pacman -S --noconfirm make devtools docker fakechroot fakeroot &&\
    mkdir /build

COPY . /build

WORKDIR /build
ENTRYPOINT /usr/bin/make "$(pwd)/output/Dockerfile.base"