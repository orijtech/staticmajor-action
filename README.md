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
```

The action takes a single input, `packages`, to specify the packages
to analyze. If omitted, the default value is `./...`.

The action is also available on [GitHub Marketplace](https://github.com/marketplace/actions/staticmajor-analyzer).
