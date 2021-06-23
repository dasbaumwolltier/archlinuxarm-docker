FROM yangxuan8282/archlinuxarm

RUN pacman -Suy --noconfirm &&\
    pacman -S --noconfirm make devtools docker fakechroot fakeroot &&\
    mkdir /build

COPY . /build

WORKDIR /build
RUN make "$(pwd)/output/base.tar.xz" "$(pwd)/output/Dockerfile.base"