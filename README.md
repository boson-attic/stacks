# Stacks

Stacks repository.

## Usage

Add the repository to your local repository cache
```
appsody repo add boson https://github.com/openshift-cloud-functions/stacks/releases/latest/download/boson-index.yaml
```

Confirm the appsody is now available
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

Generate a new ./boson-index.json and ./boson-index.yaml 
```
make generate
```
Commit the updated index files and tag the commit with a new version. For example:
```
git commit -m "index update" boson-index.json boson-index.yaml
git tag v0.0.1
git push && git push --tags
```

Release the new repo index
```
make release
```

