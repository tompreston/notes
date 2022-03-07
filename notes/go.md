# Go
* https://golang.org/doc/
* https://gobyexample.com/
* https://github.com/robpike
* https://github.com/buildbarn

## Go modules
A Go module is a collection of packages.

go.mod
* module path, is also import path for root dir
* dep requirements, other modules needed (transitive deps for downstreams)
* semver

## dep
dep is a deprecated way of managing the vendor dir with Gopkg.lock and
Gopkg.toml manifest. I've included this because it's useful to know my way.
around it for migrating from dep to Go modules.

There are some daily commands here

	https://golang.github.io/dep/docs/daily-dep.html

There's a diagram here:

	https://golang.github.io/dep/docs/ensure-mechanics.html

It's possible to force transitive deps:

	https://golang.github.io/dep/docs/Gopkg.toml.html

	[[override]]
	name = "rsc.io/sampler"
	version = "=1.3.1"

	[[constraint]]
	name = "rsc.io/quote"
	version = "3.1.0"

	[prune]
	go-tests = true
	unused-packages = true

## GOPATH changes it's behaviour depending on context
Help text explains more:

	go help gopath-get

$GOPATH/src is the old GOPATH mode.

## Commands
Create a new module, initializing the go.mod file that describes it.

	go mod init example.com/foo

Package-building commands add new dependencies to go.mod as needed  (or used to).

	go build, go test

Prints the current module’s dependencies.

	go list -m all

Change the required version of a dependency (or adds a new dependency).

	go get

Remove unused dependencies.

	go mod tidy
