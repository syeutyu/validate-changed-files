# Describe of the repository
When you use a versioning system or package.

Some commit or pull request must need to include important file.
(ex package.json or md file)

If you write not include file and after deployed?
That's a very tiring situation.

So I want to prevent the above situation therefore just created this repo.

## How to use

Just simple like below that.

```yml
name: 'build-test'
on:
  pull_request:
  push:
    branches:
      - "master"

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm ci
      - uses: ./
        with:
          file-names: '["package.json", "READMD.md"]'
          github-token: {{ Token }}
```

The current Github action doesn't yet support an array type of input.

So I used some trick.

Just enclose an array string in quotation marks.
