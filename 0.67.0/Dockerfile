FROM buildpack-deps:bionic-curl AS setup

ARG VERSION=0.67.0

WORKDIR /tmp

RUN wget https://github.com/gohugoio/hugo/releases/download/v${VERSION}/hugo_${VERSION}_checksums.txt

RUN wget https://github.com/gohugoio/hugo/releases/download/v${VERSION}/hugo_${VERSION}_Linux-64bit.tar.gz

RUN sha256sum -c hugo_${VERSION}_checksums.txt --ignore-missing

RUN tar -xf hugo_${VERSION}_Linux-64bit.tar.gz -C /usr/bin

FROM alpine AS final

COPY --from=setup /usr/bin/hugo /usr/bin/hugo

RUN mkdir -p /usr/src/hugo

WORKDIR /usr/src/hugo

ENTRYPOINT [ "hugo" ]
