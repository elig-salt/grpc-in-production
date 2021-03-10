# Buf linter

```sh
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
