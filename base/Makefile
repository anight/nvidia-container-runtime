# Copyright (c) 2017-2018, NVIDIA CORPORATION. All rights reserved.

DOCKER ?= docker

GOLANG_VERSION := 1.10.3

.NOTPARALLEL:
.PHONY: all

all: ubuntu16.04 ubuntu14.04 debian9 debian8 centos7 sles12 amzn2 amzn1

ubuntu%: $(CURDIR)/Dockerfile.ubuntu
	$(DOCKER) build --build-arg VERSION_ID="$*" \
	                --build-arg GOLANG_VERSION="$(GOLANG_VERSION)" \
	                -t "nvidia/base/ubuntu:$*" -f Dockerfile.ubuntu .

debian%: $(CURDIR)/Dockerfile.debian
	$(DOCKER) build --build-arg VERSION_ID="$*" \
	                --build-arg GOLANG_VERSION="$(GOLANG_VERSION)" \
	                -t "nvidia/base/debian:$*" -f Dockerfile.debian .

centos%: $(CURDIR)/Dockerfile.centos
	$(DOCKER) build --build-arg VERSION_ID="$*" \
	                --build-arg GOLANG_VERSION="$(GOLANG_VERSION)" \
	                -t "nvidia/base/centos:$*" -f Dockerfile.centos .

sles%: $(CURDIR)/Dockerfile.sles
	$(DOCKER) build --build-arg VERSION_ID="2.0.2-with-repos" \
	                --build-arg GOLANG_VERSION="$(GOLANG_VERSION)" \
	                --build-arg http_proxy="${http_proxy}" \
	                --build-arg https_proxy="${https_proxy}" \
	                --build-arg no_proxy="${no_proxy}" \
	                --network=host \
	                -t "nvidia/base/sles:$*" -f Dockerfile.sles .

amzn%: $(CURDIR)/Dockerfile.amzn
	$(DOCKER) build --build-arg VERSION_ID="$*" \
	                --build-arg GOLANG_VERSION="$(GOLANG_VERSION)" \
	                -t "nvidia/base/amzn:$*" -f Dockerfile.amzn .
