# GitHub Action for curl + git patch

Wraps the curl CLI to be used in GitHub Actions. See also [GitHub Action for wget](https://github.com/marketplace/actions/github-action-for-wget).

`curl https://github.com/${user}/${repository}/commit/${git-diff-hash}.diff | git apply `

e.g.

`curl https://github.com/freight-trust/curl/commit/c91413605bf93c975af7cec640e63bc306d5550f.diff | git apply`


## Features
 * make http requests
 * http errors are treated as errors


## Usage

### GitHub Actions
```
on: push
jobs:
  curl:
    runs-on: ubuntu-latest
    steps:
    - name: curl
      uses: wei/curl@master
      with:
        args: https://httpbin.org/get
```

```
on: push
jobs:
  curl:
    runs-on: ubuntu-latest
    steps:
    - name: curl
      uses: wei/curl@v1
      with:
        args: -X POST https://httpbin.org/post
```

```
on: push
jobs:
  curl:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: curl
      uses: wei/curl@v1
      with:
        args: --upload-file .github/workflows/main.yml https://transfer.sh/main-workflow.yml
```

### Docker
```
docker run --rm $(docker build -q .) \
  https://httpbin.org/get
```


## Author
[Wei He](https://github.com/wei) _github@weispot.com_


## License
[MIT](https://wei.mit-license.org)
