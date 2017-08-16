# git-exec-and-restage

[![npm](https://img.shields.io/npm/v/@easyops/git-exec-and-restage.svg)](https://www.npmjs.com/package/@easyops/git-exec-and-restage)
[![Build Status](https://travis-ci.org/easyops-cn/git-exec-and-restage.svg?branch=master)](https://travis-ci.org/easyops-cn/git-exec-and-restage)

> Safely amend Git commits after applying auto-fixing tools

`git-exec-and-restage` executes a command for you on a set of files. This
command may modify the files (imagine a linter in auto-fix mode, like `prettier
--write` or `eslint --fix`). If the files were fully staged before the command
ran, the changes will be automatically added to the Git index; if they were
_partially_ changed the Git index will remain untouched.

## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [Contribute](#contribute)
- [Acknowledgements](#acknowledgements)
- [License](#license)

## Install

```sh
yarn add --dev @easyops/git-exec-and-restage
```

## Usage

Manually e.g. with `prettier`:

```sh
git-exec-and-restage prettier --write -- file1.js file2.js
```

Automatically e.g. with `lint-staged`:

### `package.json`

```json
{
  "scripts": {
    "precommit": "lint-staged"
  },
  "lint-staged": {
    "*.js": ["git-exec-and-restage eslint --fix --"]
  }
}
```

## Contribute

PRs welcome.

## Acknowledgements

This package owes a great deal to Matthew Chase Whittemore's
[`staged-git-files`](https://github.com/mcwhittemore/staged-git-files).

## License

MIT © Moti Zilberman
