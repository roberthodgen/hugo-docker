VERSION=0.67.0

ifeq (, $(shell which docker))
	$(error "docker not in $(PATH)!")
endif

.PHONY: build
build:
	@docker build --rm=false -t roberthodgen/hugo:${VERSION} --pull --build-arg VERSION=${VERSION} .
