export NAME := sonar-scanner

.PHONY: test
test: setup ##@targets Starts docker compose.
	docker-compose -p $(NAME) -f test.yaml up

.PHONY: rm
rm:
	docker-compose -p $(NAME) -f test.yaml rm -f

.PHONY: clean
clean: rm
	sudo rm -rf root

.PHONY: setup
setup:
	for file in src; do \
	    mkdir -p root/$${file}; \
	    sudo chmod o+rwX root/$${file}; \
	done

include ../docker-make-utils/Makefile.help
include ../docker-make-utils/Makefile.functions
