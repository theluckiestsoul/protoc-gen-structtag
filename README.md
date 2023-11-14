# protoc-gen-structtag

This is a struct tag generator plugin for the Google Protocol Buffers compiler (`protoc`). The plugin can generate struct tags for your messages for JSON encoding and ORM mapping.

## Installation
If you'd like to install this locally, you can `go install` it.

```bash
$ go install github.com/theluckiestsoul/protoc-gen-structtag/cmd/protoc-gen-structtag@latest
```

## Invoking the Plugin

The plugin is invoked by passing the `--structtag_out`, and `--structtag_opt` options to the `protoc` compiler. The option has the
following format:

If you want to use the executable directly, you can invoke it with the `--plugin` option to `protoc`:

```
protoc --plugin=protoc-gen-structtag=protoc-gen-structtag  --structtag_out=internal ----structtag_opt=paths=source_relative, dbtag=bun proto/*.proto
```

If you have installed the plugin using `go install`, you can omit the `--plugin` option:

```
protoc --structtag_out=internal --structtag_opt=paths=source_relative,dbtag=bun proto/*.proto
```

## Options
struct tag plugin has the following options:
1. `dbtag`: The tag name for ORM mapping. This option is mandatory. We can provide values like `db`, `gorm`, `bun`, etc.

## Using buf (Recommended)

Once you install buf, you can use this plugin by adding the following to your `buf.gen.yaml`:

```yaml
version: v1
plugins:
  - name: structtag
    out: internal
    opt: paths=source_relative,dbtag=bun
    strategy: all
```
