build: 
		protoc --go_out=. basic.proto
		mv generated/basic.pb.go .

run:
		go run main.go basic.pb.go