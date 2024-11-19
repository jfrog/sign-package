# Example for usage

# .github/workflows/create-signature.yml
```
name: Build python with signature

on:
    [push, workflow_dispatch]

jobs:
    build:
        runs-on: ubuntu-latest
        steps:
            - name: Checkout
              uses: actions/checkout@v2

            - name: Install jfrog cli
              uses: jfrog/setup-jfrog-cli@v4
              env:
                JF_URL: ${{ vars.ARTIFACTORY_URL }}
                JF_ACCESS_TOKEN: ${{ secrets.ARTIFACTORY_ACCESS_TOKEN }}

            - name: Run Create Signature Action
              uses: ./.github/actions/create-signature
              with:
                package-name: "example-project-app"
                package-repo-name: "example-project-docker-dev-local"
                private-key: ${{ secrets.PRIVATE_KEY }}
                  

```