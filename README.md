# Volume owner

## DEVELOPER environment variable (required)

Run the following command (or add it to ~/.profile or ~/.bashrc) to set the DEVELOPER environment variable:

```bash
export DEVELOPER="$(id -u):$(id -g)"
```

## Example

```
---
version: "3"
services:
  volume:
    build:
      network: none
      dockerfile_inline: |
        FROM wyga/success
        USER ${DEVELOPER?required}
        WORKDIR /1
        WORKDIR /2
    volumes:
      - vol1:/1
      - vol2:/2

  example:
    image: alpine:3
    command: ls -l /example
    volumes:
      - vol1:/example/volume_2
      - vol2:/example/volume_1

volumes:
  vol1:
  vol2:
```
