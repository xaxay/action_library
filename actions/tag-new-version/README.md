# Tag new version 

This action adds new tag version.

## Inputs

no input arguments

## Outputs

`version` - New version. Alternativ access to it through environemnt variable `VERSION`.
`old-version` - Old version. Alternativ access to it through environemnt variable `OLD_VERSION`.
`branch` - Tagged branch name. Alternativ access to it through environemnt variable: `BRANCH`.


## Usage example

To use this action in your workflow, add the following step:

```yml
name: Your workflow
on: [push]
jobs:
  build:
    name: build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      # validation steps

      - name: Add new version tag.
        suses: xaxay/action-library/actions/action-increment-version@main

      - name: Example how to use new version
        run: |
          echo "The branch '$BRANCH' was tagged with new version '$VERSION'"

      # publish steps
```