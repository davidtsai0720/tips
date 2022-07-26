# **Command Line Interface**

- [Test](#test)
  - [Generate Test Coverage HTML](#generate-test-coverage-html)
  - [Run Single Test](#run-single-test)

## **Test**

### ***Generate Test Coverage HTML***

```sh
$ go test -coverprofile=cover.out ./... && go tool cover -html cover.out -o coverage.html
?       pratice/cmd     [no test files]
```

### ***Run Single Test***

```sh
$ go test -run regexp .
ok      pratice/cmd     0.003s [no tests to run]
```
