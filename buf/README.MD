# Buf - Linting protobuf schemas

Buf is used to validate changes against snapshots of schemas.

## Install buf
https://github.com/bufbuild/buf

Follow the instructions:
https://docs.buf.build/installation/#via-homebrew

```sh
brew tap bufbuild/buf
brew install buf
```

* Create a buf.yaml file
* lint your proto files with:
```sh
buf lint .
```
Try to fix those lint errors!

If you get stuck - switch to `lint-fixed` branch :)


Taking a snapshot:
cd buf
```sh
buf build -o image.json
```

Make a breaking change, and run:
```sh
buf breaking --against image.json
```
