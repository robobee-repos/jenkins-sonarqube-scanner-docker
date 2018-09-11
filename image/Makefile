REPOSITORY := robobeerun
NAME := sonar-scanner
VERSION ?= 3.2.0.1227-r.1

.PHONY: build
build: _build ##@targets Builds the docker image.

.PHONY: clean
clean: _clean ##@targets Removes the local docker image.

.PHONY: deploy
deploy: _deploy ##@targets Deploys the docker image to the repository.

include ../docker-make-utils/Makefile.help
include ../docker-make-utils/Makefile.functions
include ../docker-make-utils/Makefile.image
