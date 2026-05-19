---
name: setup_luci
description: prepares the environment for working within the luci repo
---

# This sets the environment up for working within the luci repo

Use bash for the following, the following commands are going to set environment
variables; once everything is set, conserve this environment for the rest of
the session for commands to work.

1. cd infra/go
2. eval `./env.py`
3. updated_go_version=$(go version)
4. updated_go_path=$(which go)

If things have worked so far, two conditions must be true:

- updated_go_path should end in `infra/go/golang/go/bin/go`
- The environment variable `GOTOOLCHAIN` has value `local`.

If either of these conditions are not met, then warn the user that the setup
has not worked.

Regardless of success/failure, show the user the values of the following
variables before proceeding:

- updated_go_version
- updated_go_path
- GOTOOLCHAIN
- GOBIN
- GOROOTH

Lastly, if the setup has worked so far, do:

7. cd src/go.chromium.org/luci
8. go build ./...

If that succeeds, then everything is ready.

Unless otherwise specified, the rest of the session should use commands
with `infra/go/src/go.chromium.org/luci` as the PWD/current working directory.
