# duckdb CLI builds for alpine

This is a small build-only repo for creating alpine-compatible `duckdb`
binaries.

## Why?

The official binaries don't work on alpine, and I couldn't find any
combination of glibc compat libs that would satisfy their needs.
Building `duckdb` on Alpine works, but it's annoying to have to do
that in every pipeline.

## How to use

```shell
curl -LO https://github.com/srenatus/duckdb-cli-alpine/releases/download/v1.0.0/duckdb-linux-amd64
curl -LO https://github.com/srenatus/duckdb-cli-alpine/releases/download/v1.0.0/json.duckdb_extension
chmod +x duckdb-linux-amd64
mv duckdb-linux-amd64 /usr/local/bin/duckdb
duckdb -c "INSTALL './json.duckdb_extension';"
```

## Limitations

- only `json` extension is built, using the official build for other extensions
  (such as through autoloading) **will fail**
- only linux/amd64

## License

The small build code in this repo is Apache-2.0 licensed, but that
does not have anything to do with the duckdb sources -- their license
is [MIT](https://github.com/duckdb/duckdb?tab=MIT-1-ov-file#readme).
