# Example Application

Example Go Application illustrating use of the [cobra][cobra] and [viper][viper] packages.

See [cobra/README.md][cobra-readme] for detailed information.

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

* Create `$HOME/.cobra.yaml` configuration file

  ```
  cat > $HOME/.cobra.yaml << EOF
  author: Chris Stefano <virtualstaticvoid@gmail.com>
  license: MIT
  year: 2021
  EOF
  ```

* Generate `cobra` boilerplate code

  ```
  cobra init --pkg-name go.virtualstaticvoid.com/prototype/cobra-app
  ```

* Create `cobra` commands

  ```
  cobra add serve
  cobra add config
  cobra add create --parent 'configCmd'
  ```

* Make manual edits to respective command files.

  * [`3d16ac3`][_3d16ac3] add `verbose` global flag to `cmd/root.go`
  * [`1e2f07f`][_1e2f07f] add current working directory to the configuration file search path
  * [`5cf55c8`][_5cf55c8] print out file configuration settings in `cmd/root.go` command initialisation
  * [`028ee2b`][_028ee2b] add "foo" switch to the `cmd/config.go` command and configuration bindings
  * [`028ee2b`][_028ee2b] print out final configuration settings in the `config` command handler
  * [`0d97ee3`][_0d97ee3] print out final configuration settings in the `config create` command handler
  * [`3276a49`][_3276a49] add an example confguration file

  See git commit history for the complete list of changes.

## Usage

In each example, run the command and observe the console output.

### Defaults

```
go run main.go config
```

```
go run main.go config create
```

### From Environment Variables

```
FOO=FROM-ENV go run main.go config
```

```
FOO=FROM-ENV go run main.go config create
```

### From Configuration File

```
go run main.go --config .cobra-example.yaml config
```

```
go run main.go --config .cobra-example.yaml config create
```

## License

The MIT License (MIT) - Copyright © 2021 Chris Stefano

See [LICENSE](LICENSE) for details.

<!-- links -->

[cobra-readme]: https://github.com/spf13/cobra/blob/master/cobra/README.md
[cobra]: https://github.com/spf13/cobra
[viper]: https://github.com/spf13/viper
[_3d16ac3]: https://github.com/virtualstaticvoid/cobra-example/commit/3d16ac30b32d98d927d3ea15e8f247d8b9647729
[_1e2f07f]: https://github.com/virtualstaticvoid/cobra-example/commit/1e2f07fa6ef53a1c390654ee9106d00208120749
[_5cf55c8]: https://github.com/virtualstaticvoid/cobra-example/commit/5cf55c815e07d9e177afb99cd4fc64bc23f7a0f9
[_028ee2b]: https://github.com/virtualstaticvoid/cobra-example/commit/028ee2bb6cd2d6d09e0d8e29bb23a8edf62229fb
[_028ee2b]: https://github.com/virtualstaticvoid/cobra-example/commit/028ee2bb6cd2d6d09e0d8e29bb23a8edf62229fb
[_0d97ee3]: https://github.com/virtualstaticvoid/cobra-example/commit/0d97ee361b2e9913ecfd98cfc71b558c28b18b93
[_3276a49]: https://github.com/virtualstaticvoid/cobra-example/commit/3276a49d315dded1f9b851c884aebc563bb59931
