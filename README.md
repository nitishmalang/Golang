# Golang
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
permissions:
  # Goreadme needs permissions to update pull requests comments and change contents.
  pull-requests: write
  contents: write
jobs:
    goreadme:
        runs-on: ubuntu-latest
        steps:
        - name: Check out repository
          uses: actions/checkout@v2
        - name: Update readme according to Go doc
          uses: posener/goreadme@v1
          with:
            badge-travisci: 'true'
            badge-codecov: 'true'
            badge-godoc: 'true'
            badge-goreadme: 'true'
            # Optional: Token allows goreadme to comment the PR with diff preview.
            GITHUB_TOKEN: '${{ secrets.GITHUB_TOKEN }}'
