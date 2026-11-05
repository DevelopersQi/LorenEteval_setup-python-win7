# setup-python-win7

[![Test composite action](https://github.com/DevelopersQi/LorenEteval_setup-python-win7/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/LorenEteval/setup-python-win7/actions/workflows/test.yml)

GitHub action that sets up a Windows7–compatible version of Python.

## Usage

```yaml
- name: Setup Python for Windows7  
  uses: DevelopersQi/LorenEteval_setup-python-win7@18aab37082fbf522fc1bf4df7631aafd3186c661
  with:
    # required: "3.x" or "3.x.y"
    python-version: "3.11"
    # optional: freethreaded version or not, default is false
    freethreaded: false
    # optional: dummy input, if python version is specified as 'x.y', then always use latest
    check-latest: true
    # optional: x86, x64, or arm64, default is host OS architecture
    architecture: x64
    # optional: setup Python for windows7 from this repo
    github-repo: adang1345/PythonVista
    # optional: setup Python for windows7 from this repo branch
    github-repo-branch: "master"
- name: Check Python for Windows7 version
  shell: bash
  run: |
    python_path=$(which python)
    python_home=$(dirname "$python_path")

    echo "Python home is: $python_home"

    python -c "import sys; print(sys.version)"
```


## Compatibility notes

The action installs a third-party Windows 7-compatible Python build. GitHub-hosted Windows runners can validate installation and basic interpreter execution, but they are not Windows 7. Confirm application behavior on a real Windows 7 x64 machine or VM before claiming runtime compatibility. This repository currently documents a pinned commit because no `v1` release tag is published.
