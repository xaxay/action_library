# Tag new version 

This GitHub Action creates a new version tag for the current branch by incrementing the patch number of the latest version tag found.

## Inputs

No input arguments required.

## Outputs

- `version`: The new version tag created. Alternatively, access it through the environment variable `VERSION`.
- `old-version`: The previous version tag before the new one was created. Alternatively, access it through the environment variable `OLD_VERSION`.
- `branch`: The name of the current branch that has been tagged. Alternatively, access it through the environment variable `BRANCH`.


## Usage example

## Usage Example

To use this action in your workflow, add the following steps to your `.github/workflows/main.yml` file:

```yml
name: Your workflow
on: [push]
jobs:
  build:
    name: build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2

      # Add validation steps here

      - name: Tag New Version
        uses: xaxay/action-library/actions/tag-new-version@main
        id: new-version

      - name: Use New Version
        run: |
          echo "The branch '${{ steps.new-version.outputs.branch }}' was tagged with new version '${{ steps.new-version.outputs.version }}'"

      - name: Use New Version through environemnt variables
        run: |
          echo "The branch '$BRANCH' was tagged with new version '$VERSION'"

      # Add CD steps here 
```
