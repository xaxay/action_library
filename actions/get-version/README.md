# Get version 

This GitHub Action retrieves current and new versions based on tags for the current branch.

## Inputs

- `branch` The branch name for which vesrion information is required. By default current branch name is used.

## Outputs

- `new-version`: The new version. Alternatively, access it through the environment variable `NEW_VERSION`.
- `version`: The previous version. Alternatively, access it through the environment variable `VERSION`.
- `branch`: The name of the current branch for which version information is retrieved. Alternatively, access it through the environment variable `BRANCH`.


## Usage Example

To use this action in your workflow for current branch, add the following steps to your `.github/workflows/some-workflow-file.yml` file:

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

      - name: Get Version information
        uses: xaxay/action-library/actions/get-version@main
        id: version-info

      - name: Use version information
        run: |
          echo "The branch '${{ steps.version-info.outputs.branch }}' was tagged with version '${{ steps.version-info.outputs.version }}', next version will be '${{ steps.version-info.outputs.new-version }}'"

      - name: Use New Version through environemnt variables
        run: |
          echo "The branch '$BRANCH' was tagged with version '$VERSION', next version will be $NEW_VERSION" 
```


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

      - name: Get Version information
        uses: xaxay/action-library/actions/get-version@main
        id: version-info

      - name: Use version information
        run: |
          echo "The branch '${{ steps.version-info.outputs.branch }}' has version tag '${{ steps.version-info.outputs.version }}', next version will be '${{ steps.version-info.outputs.new-version }}'"

      - name: Use New Version through environemnt variables
        run: |
          echo "The branch '$BRANCH' has version tag '$VERSION', next version will be $NEW_VERSION" 
```