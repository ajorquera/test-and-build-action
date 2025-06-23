# Test and Build Action

```
name: 'Deploy PR Preview'
on:
  pull_request:

permissions:
  pull-requests: write

concurrency:
  group: pr-${{ github.event.number}}
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Install & Build
        uses: ajorquera/test-and-build-action@v1

      - name: Build Preview
        uses: ajorquera/create-preview-action@v1
```