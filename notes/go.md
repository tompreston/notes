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
