## Gateway

`GRPCIp` - ip gRPC. By default: `127.0.0.1`<br>
`GRPCPort` - port gRPC. By default: `9001`

`HTTPIp` - ip http server. By default: `127.0.0.1`<br>
`HTTPPort` - port http server. By default: `8001`


### Install

#### Dependencies
```bash
go install github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-grpc-gateway github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-openapiv2 google.golang.org/protobuf/cmd/protoc-gen-go google.golang.org/grpc/cmd/protoc-gen-go-grpc
```

#### Generate stub

##### GRPC:
```
protoc -I . -I  $GOPATH/pkg/mod/github.com/grpc-ecosystem/grpc-gateway/v2@v2.2.0/third_party/googleapis -I $GOPATH/src/github.com/protocolbuffers/protobuf/src --go_out . --go_opt paths=source_relative --go-grpc_out . --go-grpc_opt paths=source_relative gateway/proto/gateway.proto
```

##### GATEWAY

```
protoc -I . -I $GOPATH/pkg/mod/github.com/grpc-ecosystem/grpc-gateway/v2@v2.2.0/third_party/googleapis -I $GOPATH/src/github.com/protocolbuffers/protobuf/src --grpc-gateway_out . --grpc-gateway_opt logtostderr=true --grpc-gateway_opt paths=source_relative --grpc-gateway_opt generate_unbound_methods=true gateway/proto/gateway.proto
```