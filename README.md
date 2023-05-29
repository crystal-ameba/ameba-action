# Crystal Ameba GitHub Action

GitHub Action that lints Crystal shards with [Ameba](https://github.com/crystal-ameba/ameba) linter

![](https://github.com/crystal-ameba/github-action/raw/master/assets/sample.png)

## Usage

Add the following to your GitHub action workflow to use Crystal Ameba Linter:

``` yaml
- name: Crystal Ameba Linter
  uses: crystal-ameba/github-action@v0.7.1
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Example Workflow

``` yaml
name: Crystal CI

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    container:
      image: crystallang/crystal

    steps:
    - uses: actions/checkout@v1
    - name: Crystal Ameba Linter
      id: crystal-ameba
      uses: crystal-ameba/github-action@v0.7.1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    - name: Install dependencies
      run: shards install
    - name: Run tests
      run: crystal spec
```

## Compatibility Versions

| Ameba version | GitHub Action version |
|---------------|-----------------------|
| ~> v1.4.0     | v0.7.1                |
| v1.3.1        | v0.6.0                |
| v1.2.0        | v0.5.1                |
| v1.1.0        | v0.4.0                |
| v1.0.1        | v0.3.1                |
| v1.0.0        | v0.3.0                |
| v0.14.3       | v0.2.12               |

### Bump versions

* Crystal version should be updated in `Dockerfile` file (version of the image).
* Ameba version should be updated in `shard.yml`/`shard.lock` files.

## Contributing

1. Fork it (<https://github.com/crystal-ameba/github-action/fork>)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## Contributors

- [Vitalii Elenhaupt](https://github.com/veelenga) - creator and maintainer
