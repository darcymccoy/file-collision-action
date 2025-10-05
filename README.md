# Merge Conflict GitHub Action

A GitHub action that warns if merging a PR will create merge conflicts in another PR.

## Usage

Create a `.github/workflows/merge-conflict-action.yml` file in your repository with the following configuration:

```yml
name: Merge Conflict Scan

on:
  pull_request:
    branches:
      - main

permissions:
  contents: read

jobs:
  merge-conflict:
    name: Merge Conflict Scan
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        id: checkout
        uses: actions/checkout@v5

      - name: Warn if Creating Merge Conflict
        id: merge-conflict
        uses: darcymccoy/merge-conflict-action@v1

      - name: Print Output
        id: output
        run: echo "${{ steps.merge-conflict.outputs.message }}"
```

Or, add the following to a pre-existing workflow file under the job section:

```yml
merge-conflict:
  name: Merge Conflict Scan
  runs-on: ubuntu-latest

  steps:
    - name: Checkout
      id: checkout
      uses: actions/checkout@v5

    - name: Warn if Creating Merge Conflict
      id: merge-conflict
      uses: darcymccoy/merge-conflict-action@v1

    - name: Print Output
      id: output
      run: echo "${{ steps.merge-conflict.outputs.message }}"
```

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/darcymccoy/merge-conflict-action.git
   ```

1. Install the dependencies:

   ```bash
   npm install
   ```

1. Run the tests:

   ```bash
   npm test
   ```

1. package the project for distribution:

   ```bash
   npm run bundle
   ```

## Learn More

To make your own GitHub action check out [GitHub's documentation.](https://docs.github.com/en/actions/how-tos/create-and-publish-actions)
