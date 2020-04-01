# Stacks

Stacks repository.

## Usage

Add the repository to your local repository cache
```
appsody repo add boson https://github.com/boson-project/stacks/releases/latest/download/boson-index.yaml
```

Confirm the stack is now available
```
appsody repo list
```

Use a stack
```
appsody init boson/node-ce-functions
```


## Releasing

requires: python3 and hub

When a new stack is added (or its metadata changes), package and deploy the stack first (see the stack repo for instructions) and after doing so the local dev.local repo will have the updated boson-index.yaml, which can be released via this repository using the following process:

1) Generate a new ./boson-index.json and ./boson-index.yaml
```
make generate
```
2) Commit the updated index files and tag the commit with a new version. For example:
```
git commit -m "Release Go v0.0.1" boson-index.json boson-index.yaml
git tag v0.0.5
git push && git push --tags
```

3) Release the new repo index
```
make release
```

