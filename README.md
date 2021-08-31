This repository contains a handful of example modules which exhibit simple vulnerability patterns which should be
detected using `golang.org/x/exp/vulndb/govulncheck`.

The vulnerability used for testing is in `vulns/`, and is identified using the example vulnerability database in
`db/`.

## github.com/rolandshoemaker/vuln-testing-examples/symbol-main

This module contains a `main` package which calls the vulnerable symbol `vulns.Vulnerable` in the `main` function.

As of golang.org/x/exp@v0.0.0-20210831221722-b4e88ed8e8aa this should trigger a single finding.

## github.com/rolandshoemaker/vuln-testing-examples/symbol-pkg

This module contains a `symbol` package in its root. The exported method `Affected` calls the vulnerable symbol
`vulns.Vulnerable`.

As of golang.org/x/exp@v0.0.0-20210831221722-b4e88ed8e8aa this should trigger a single finding.

## github.com/rolandshoemaker/vuln-testing-examples/importonly

This moudle contains a `importonly` package in its root. No vulnerable symbols are called, but the vulnerable package
is imported.

As of golang.org/x/exp@v0.0.0-20210831221722-b4e88ed8e8aa this should only trigger a finding when using `-imports`.

## github.com/rolandshoemaker/vuln-testing-examples/moduleonly

This module contains an empty `moduleonly` package in its root. The vulnerable package is not imported, but the
vulnerable module is required in the modules `go.mod`.

As of golang.org/x/exp@v0.0.0-20210831221722-b4e88ed8e8aa this should report nothing.