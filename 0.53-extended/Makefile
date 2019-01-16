VERSION=0.53

ifeq (, $(shell which docker))
	$(error "docker not in $(PATH)!")
endif

.PHONY: build
build:
	@docker build --rm=false -t roberthodgen/hugo:${VERSION}-extended --build-arg VERSION=${VERSION} .

