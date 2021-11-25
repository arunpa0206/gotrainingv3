PROTO_PATH := api/proto

# Output directories.
GRPC_OUT := api/generated

protoc:
	protoc --go-grpc_out=api/generated api/proto/hello-service.proto

run:
	cd server && go run server.go


unary-client:
	cd client && go run unary-client.go
	cd ..

client-streaming:
	cd client && go run clientstreaming.go
	
server-streaming:
	cd client && go run serverstreaming-client.go

bidir-streaming:
	cd client && go run bisir-streaming-client.go



