# Buf linter

## Linting

```sh

cd buf

## Buf
# Create a buf.yaml file
buf beta mod init

# Make sure buf picks up your files
buf ls-files
# hello_service.proto
# launguage.proto

# Lint your files:
buf lint .

# You can run the linter automatically on every save:
## npm i -g nodemon
## nodemon -e .proto -x 'buf lint .'

```

### Fixing the lint problem

- create `com/language` folder
- move `language.proto` to `com/language/`
- language.proto:5 - add `.v1` suffix
- hello_service:18: - add same `.v1` suffix between lowercase language and uppercase language
- create folder `v1` in `com/language`
- move `language.proto` into `com/language/v1` folder
- hello_service:5 - add `.v1` to path
- language.proto:10 - add uppercase `CODE_` prefix to `EN` value
- language.proto:10 - add `CODE_UNSPECIFIED = 0;` before `CODE_EN`
- language.proto:11 - `CODE_EN = 0;` to `CODE_EN = 1;`
- create `services` folder
- move `hello_service.proto` to `services/` folder

- create folder `v1` in `services`
- move `hello_service.proto` into `services/v1` folder
