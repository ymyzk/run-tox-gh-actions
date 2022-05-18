# run-tox-gh-actions
**run-tox-gh-actions** is a [composite run steps action](https://docs.github.com/en/actions/creating-actions/creating-a-composite-run-steps-action) which makes it easier to install and run tox with [tox-gh-actions](https://github.com/ymyzk/tox-gh-actions) plugin on GitHub Actions.

## Features
* Install tox and tox-gh-actions
* Run tox with tox-gh-actions

## Usage
1. Follow [README of tox-gh-actions](https://github.com/ymyzk/tox-gh-actions) to configure tox and tox-gh-actions
2. Use this step in your GitHub Actions workflow

## Basic Example
In `.github/workflows/<workflow>.yml`, you can use this step like

```yaml
name: CI
on:
  pull_request:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: [3.6, 3.7, 3.8, 3.9, pypy3]
    steps:
    - uses: actions/checkout@v3
    - name: Set up Python ${{ matrix.python-version }}
      uses: actions/setup-python@v3
      with:
        python-version: ${{ matrix.python-version }}
    # Instead of installing and running tox and tox-gh-actions,
    # you can simply use this composite run steps action.
    - name: Run tox with tox-gh-actions
      uses: ymyzk/run-tox-gh-actions@main
```

## Available Inputs
You can give additional inputs to tune behavior of the run-tox-gh-actions.
See [action.yml](./action.yml) for all available inputs.

```yaml
jobs:
  build:
    steps:
    - name: Run tox with tox-gh-actions
      uses: ymyzk/run-tox-gh-actions@main
      with:
        tox-version: "==3.20.1"
```
