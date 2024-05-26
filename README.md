# @LazyPanda07/get-gtest
Clone and build Google Test in Windows and Linux. MSVC on Windows

# Usage
```yaml
- uses: LazyPanda07/get-gtest@v1.1
  with:
    # Google Test repository path.
    # Optional. Default is "gtest"
    repository-path:

    # Build configuration of Google Test.
    # Optional. Default is "Release"
    build-type:

    # Google Test branch name to clone.
    # Optional. Default is "v1.14.x"
    branch-name:
      
    # Build result path(include, lib folders) relative to github.workspace.
    # Required.
    install-path:

    # Compiler name only for Linux.
    # Optional. Default is "gcc"
    compiler:
      
    # Windows specific setting, static or shared CRT build.
    # Optional. Default is "ON"
    force-shared-crt:
```

## Source
See [action.yml](https://github.com/LazyPanda07/get-gtest/blob/master/action.yml)

# Example
```yaml
on:
  push:
    branches: [master]
  workflow_dispatch:

jobs:
  test:
    strategy:
      matrix:
        platform: [ubuntu-latest, windows-latest]
    
    runs-on: ${{ matrix.platform }}

    steps:
    - uses: LazyPanda07/get-gtest@v1.1
      with:
        install-path: new-path/make-install

    - name: Print result
      run: ls new-path/make-install
```
