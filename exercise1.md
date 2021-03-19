# [Part 11 exercise 1](https://fullstackopen.com/en/part11/introduction_to_ci_cd#exercise-11-1)

Our hypothetical application will contain somekind of a Go based backend which will be the focus of this text. I have no actual Go experience so this exercise will hopefully be useful but could also contain some assumptions which would not hold in an actual implementation.

One obvious answer for linting Go might be [Golint](https://github.com/golang/lint) however on closer examination it seems to be a 'one size fits some' solution without much customization options which could become a problem if it's used in CI/CD environment (where we need the linter to not have any errors/warnings).  There's also the gofmt for code formatting, gopls language server for IDEs and govet for code correctness. Overall it seems that the linting environment for Go is fragmented and it's customary to run multiple linters using a linter runner. [golangci-lint](https://github.com/golangci/golangci-lint) seems to be a common runner.

Unit testing would probably be done with the [testing](https://golang.org/pkg/testing/) package which is built into Go.

The default build system for Go (go build) seems to be commonly used and suitable for our purposes. It will by default generate an executable binary in the used architecture. Also an alternative compiler frontend gccgo is available for the GCC compiler.

Some CI services I have used before include [CircleCI](https://circleci.com/) and [TravisCI](https://www.travis-ci.com/) however I haven't yet found any major advantages compared to the others in any of these.

By default I would go with a cloud-based solution. Running a self hosted CI service would demand more resources from the actual development work and I don't think that's warranted in this case with a imaginary team of 6 people. In some cases some kind of weird hardware requirements could force us to use a self-hosted solution.