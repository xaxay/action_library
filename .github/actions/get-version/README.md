# Get version 

This GitHub Action retrieves current and new versions based on tags for a specified branch.

## Inputs

- `branch`: The branch name for which version information is required. Defaults to the current branch if not specified.

## Outputs

- `version`: The current version based on the latest tag.
- `new-version`: The next version tag, calculated by incrementing the patch number.
- `branch`: The name of the branch for which version information was retrieved.

## Usage Example

To use this action in your workflow, add the following steps to your `.github/workflows/your-workflow.yml` file:

```yml
name: Example Workflow
on: [push]
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2

      - name: Get Version Information
        uses: your-username/action-library/actions/get-version@main
        id: version-info

      - name: Use Version Information
        run: |
          echo "Branch '${{ steps.version-info.outputs.branch }}' has version tag '${{ steps.version-info.outputs.version }}'. Next version will be '${{ steps.version-info.outputs.new-version }}'."

      - name: Use Version Variables
        run: |
          echo "Branch '$BRANCH' has version tag '$VERSION'. Next version will be '$NEW_VERSION'."
