# Example Application

See [cobra/README.md](https://github.com/spf13/cobra/blob/master/cobra/README.md) for detailed information.

## Setup

See the git commit log of this repository for each step, or follow these instructions:

* Initialise new go application

  ```
  go mod init go.virtualstaticvoid.com/prototype/cobra-app
  ```

* Install `cobra/cobra@latest` package

  ```
  go get github.com/spf13/cobra/cobra@latest
  ```

* Generate `cobra` boilerplate code

  ```
  cobra init --pkg-name go.virtualstaticvoid.com/prototype/cobra-app --author "Chris Stefano <virtualstaticvoid@gmail.com>" --license MIT
  ```

* Create `cobra` commands

  ```
  cobra add serve
  cobra add config
  cobra add create --parent 'configCmd'
  ```

* Make manual edits to respective command files.

  * add `verbose` global flag to `cmd/root.go`
  * add current working directory to the configuration file search path
  * print out file configuration settings in `cmd/root.go` command initialisation
  * add "foo" switch to the `cmd/config.go` command and configuration bindings
  * print out final configuration settings in the `config` command handler
  * print out final configuration settings in the `config create` command handler
  * add an example confguration file

  See git commit history for the complete list of changes.

# Usage

In each example, run the command and observe the console output.

## Defaults

```
go run main.go config
```

```
go run main.go config create
```

# From Environment Variables

```
FOO=FROM-ENV go run main.go config
```

```
FOO=FROM-ENV go run main.go config create
```

# From Configuration File

```
go run main.go --config .cobra-example.yaml config
```

```
go run main.go --config .cobra-example.yaml config create
```

## TODO

* Figure out how to persist the author and license information when running `cobra ...` commands to generate code.

## License

The MIT License (MIT) - Copyright © 2021 Chris Stefano
See [LICENSE](LICENSE) for details.
