PACKER_JSON=gentoo-amd64-template.json

all: help

help:
	@echo ""
	@echo "-- Help Menu"
	@echo ""
	@echo "   1. make build       - build the postgresql image"
	@echo "   2. make clean  - cleanup"

build: build-vbox beep

#clean: cleanvendor cleanbuilds
clean: cleanbuilds

build-qemu:
	@echo "build-qemu"
	/usr/bin/time -v packer build --only=qemu $(PACKER_JSON)

build-qemu-debug:
	/usr/bin/time -v packer build -debug --only=qemu $(PACKER_JSON)

build-vbox:
	/usr/bin/time -v packer build --only=virtualbox-iso $(PACKER_JSON)

build-vbox-debug:
	/usr/bin/time -v packer build -debug --only=virtualbox-iso $(PACKER_JSON)

cleanvendor:
	@echo "cleanvendor"
	rm -r vendor
	rm Berksfile.lock

vendor:
	@echo "vendor"
	berks vendor vendor/cookbooks

cleanbuilds:
	@echo "cleaning Builds"
	rm -Rf ../builds/*

beep:
	@echo "beep"
	@aplay /usr/share/sounds/alsa/Front_Center.wav
# @ogg123 /usr/share/sounds/KDE-Im-Irc-Event.ogg
