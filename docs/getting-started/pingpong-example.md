# pingpong Example

Require installing [pollapo](https://pbkit.dev/docs/getting-started/installation), [go](https://go.dev/doc/install), [protoc](https://github.com/protocolbuffers/protobuf/releases/tag/v21.8), [nodejs](https://nodejs.org/ko/download/) and [yarn](https://yarnpkg.com/getting-started/install).

And Install `protoc-gen-go` and `protoc-gen-go-grpc`.

- MacOS
  - Run `brew install protoc-gen-go protoc-gen-go-grpc`
- Windows
  - Run `go install google.golang.org/protobuf/cmd/protoc-gen-go@latest`
  - Run `go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest`

Clone pingpong-server and api-common-protos.

```sh
git clone https://github.com/pbkit/pingpong-server.git
git clone https://github.com/googleapis/api-common-protos.git
```

Gen go file for protoc.

```sh
cd ./pingpong-server

pollapo install

protoc --go_out="." --go_opt=paths=source_relative --go-grpc_out="." --go-grpc_opt=paths=source_relative -I=".pollapo" .pollapo/pbkit/interface-pingpong-server/pingpong.proto -I="../api-common-protos/"
```

And start pingpong server.

```sh
go run main.go
```

Turn to another terminal and clone pingpong-client.

Then start dev server.

```sh
git clone https://github.com/pbkit/pingpong-client.git
cd pingpong-client
yarn && yarn gen && yarn dev
```
