# Build Python Action

This action builds Python wheels and source distribution for a Python package.

Here is an example demonstrating how to use it in a workflow:

```yaml
jobs:
  build:
    name: Build
    runs-on: ubuntu-20.04

    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      - name: Build wheels
        uses: frequenz-floss/gh-action-build-python@v0.x.x
        with:
          python_version: "3.11"
```

## Inputs

* `python_version`: The Python version to use. Required.

   This is passed to the `actions/setup-python` action.

* `outdir`: The directory where the built packages will be placed.

## Security

This action runs `python -I -m build`, which causes Python build tooling to
load and execute repository-controlled build configuration from the checked-out
repository.

Only use this action with trusted, already-merged code, such as workflows
triggered by `push` on protected branches or release tags. Do not use this
action with `pull_request_target`.

When you use this action, you are also trusting these external GitHub Actions:

* [`frequenz-floss/gh-action-setup-python-with-deps`][setup-python-with-deps],
  which this action runs to install Python and the requested Python packages.

[setup-python-with-deps]: https://github.com/frequenz-floss/gh-action-setup-python-with-deps
