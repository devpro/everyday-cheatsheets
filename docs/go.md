# Go

> Build fast, reliable, and efficient software at scale

[go.dev](https://go.dev/), [golang.org](https://golang.org/), [golang/go](https://github.com/golang/go)

-> [Project](https://golang.org/project/), [Documentation](https://golang.org/doc/), [Packages](https://pkg.go.dev/), [Blog](https://blog.golang.org/)

## Quick start

### Installation

[Installation](https://golang.org/doc/install) > [Downloads](https://golang.org/dl/)

<details>
  <summary>Installation on Windows 10</summary>
   
  - Download and execute MSI file (for example `go1.15.windows-amd64.msi`)
    - _Note: The installer will update the environment variables (need to restart any open command prompts for the change to take effect)_
  
    Variable Name | Variable Value | Variable Type
    ------------- | -------------- | -------------
    `GOPATH` | `%USERPROFILE%\go` | User
    `Path` | `%USERPROFILE%\go\bin` | User
    `Path` | Go installation directory + "\bin" (by default "C:\Go\bin") | System
  
  - Uninstallation steps
    - Remove remove an existing Go installation from your system delete the go directory (C:\Go by default in Windows).
    - Remove Go bin directory from the `Path` System and User environment variable and the `GOPATH` User environment variable.
</details>

#### Multipe Go versions

- Once Go has been installed, you can install other versions with for example `go get golang.org/dl/go1.10.7` and specify it afterwards `go1.10.7 version`

#### Visual Studio Code

As soon as a Go file is opened, Visual Studio Code will suggest to install Go extension.

On a Go file save, Visual Studio code will suggest installing additional tools.

<details>
  <summary>Additional tools installed by Visual Studio Code</summary>

  Installed at C:\Users\<username>\go\bin in module mode:

  - gocode
  - gopkgs
  - go-outline
  - go-symbols
  - guru
  - gorename
  - gotests
  - gomodifytags
  - impl
  - fillstruct
  - goplay
  - godoctor
  - dlv
  - gocode-gomod
  - godef
  - goreturns
  - golint
  
</details>

## Learn

[Learn](https://learn.go.dev/)

### Getting started

- [A Tour of Go](https://tour.golang.org/welcome/1)
- [The Go Playground](https://play.golang.org/)
- [How to Write Go Code](https://golang.org/doc/code.html)

### Additional readings

- [The Go Programming Language Specification](https://golang.org/ref/spec)
- [Effective Go](https://golang.org/doc/effective_go.html)
- [Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments)
- [golang-standards/project-layout](https://github.com/golang-standards/project-layout)

## CLI

Command line | Action
------------ | ------
`go mod init github.com/<username>/<repository>` | Creates go.mod file

### Tools

#### Commands

Name | Action
---- | ------
[Gofmt](https://golang.org/cmd/gofmt/) | Formats Go programs. It uses tabs for indentation and blanks for alignment. Alignment assumes that an editor is using a fixed-width font. 
