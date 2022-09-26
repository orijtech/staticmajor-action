# The Staticmajor Go analyzer

Staticmajor is a Go source code analyzer developed by Orijtech for use
in detecting security and performance issues.

## Setup

Add the `orijtech/staticmajor-action` GitHub to a workflow with your
source code checked out. Example:

```
name: Staticmajor
on: [push,workflow_dispatch,pull_request]
jobs:
  run_staticmajor:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository code
        uses: actions/checkout@v3
      - name: Staticmajor action
        id: staticmajor
        uses: orijtech/staticmajor-action@main
        with:
            packages: ./leak
            resleak: true
            httperroryzer: true
            structslop: true
```

The action takes an input, `packages`, to specify the packages
to analyze. If omitted, the default value is `./...`.

Set the `fuzzy` input value to `true` to detect leaks of values
whose types implement a `Close` or `Stop` method.

The analyzers `resleak`, `httperroryzer`, `structslop` are individually
disabled by setting their name to `false`. The example above enables all
analyzers, which is the default.

To skip analyzing tests, set the `tests` input to `false`.

The action is also available on [GitHub Marketplace](https://github.com/marketplace/actions/staticmajor-analyzer).
