FROM buildpack-deps:bionic-curl AS setup

ARG VERSION=0.53

WORKDIR /tmp

RUN wget https://github.com/gohugoio/hugo/releases/download/v${VERSION}/hugo_extended_${VERSION}_checksums.txt

RUN wget https://github.com/gohugoio/hugo/releases/download/v${VERSION}/hugo_extended_${VERSION}_Linux-64bit.tar.gz

RUN sha256sum -c hugo_extended_${VERSION}_checksums.txt --ignore-missing

RUN tar -xf hugo_extended_${VERSION}_Linux-64bit.tar.gz -C /usr/bin

FROM alpine AS final

COPY --from=setup /usr/bin/hugo /usr/bin/hugo

RUN apk add --no-cache libc6-compat libstdc++  \
    && mkdir -p /usr/src/hugo

WORKDIR /usr/src/hugo

ENTRYPOINT [ "hugo" ]
