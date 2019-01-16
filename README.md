# hugo-docker
Docker images for Hugo static site generator.

Small images based on alpine (final size about 26MB).

## Usage

Pull the latest image, or see other (Images)[#images] below:

```
$ docker pull roberthodgen/hugo
```

### Development server

Note: Hugo by default sets a listen address, you'll need to use `--bind=0.0.0.0`.

Example:

```
$ docker run -p=1313:1313 -v=$(pwd):/usr/src/hugo roberthodgen/hugo serve --bind=0.0.0.0
```

### Building for CI or CD

Below is an example `Makefile` to build using this image.

Following this process you can:
- Sync `./public` with a S3 bucket
- Run a static server like nginx

```
ifeq (, $(shell which docker))
	$(error "docker not in $(PATH)!")
endif

.PHONY: build
build: clean
	@docker run --rm=true -v=$(shell pwd):/usr/src/hugo roberthodgen/hugo

.PHONY: clean
clean:
	@rm -rfd public

.PHONY: serve
serve:
	@docker run --rm=true -p=1313:1313 -v=$(shell pwd):/usr/src/hugo roberthodgen/hugo serve --bind=0.0.0.0
```

## Images

### `roberthodgen/hugo:0.53 (latest)`

Hugo 0.53 https://github.com/gohugoio/hugo/releases/tag/v0.53

### roberthodgen/hugo:0.53-extended

Hugo 0.53 Extended https://github.com/gohugoio/hugo/releases/tag/v0.53
