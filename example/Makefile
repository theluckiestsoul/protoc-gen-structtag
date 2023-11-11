generate:
	protoc --go_out=pkg --go_opt=paths=source_relative --proto_path=proto \
    --structtag_out=internal --structtag_opt=paths=source_relative,dbtag=bun \
    proto/*.proto