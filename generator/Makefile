START			:= 1000
STOP  		:= 1004
SEQUENCE 	:= $(shell seq $(START) $(STOP))
PLATFORMS := linux/amd64,linux/arm64/v8,linux/arm/v7,linux/arm/v6
BUILDER 	:= multiplatform-builder
OUTPUT 		:= --output type=image,push=true,compression=gzip,compression-level=9,force-compression=true
BUILDX 		:= docker buildx build --provenance false --platform $(PLATFORMS) $(OUTPUT) --builder $(BUILDER)

all:
	@$(foreach seq, $(SEQUENCE), $(BUILDX) -t wyga/volume-owner-$(seq):$(seq) --pull --build-arg UID=$(seq) .;)
