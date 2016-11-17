---
layout: page
title:  "Contributing"
section: "contributing"
position: 5
---

# Contributing to Algebird

This page lists recommendations and requirements for how to best contribute to Algebird.

We strive to obey these as best as possible. As always, thanks for contributing--we hope these guidelines make it easier and shed some light on our approach and processes.

### Key branches
- `master` is the latest, deployed version.
- `develop` is where development happens and all pull requests should be submitted.

### Pull requests

- Submit pull requests against the `develop` branch.
- Try not to pollute your pull request with unintended changes--keep them simple and small.

### Post-release

After the release occurs, you will need to update the documentation. Here is a list of the places that will definitely need to be updated:

 * `docs/src/site/index.md`: update version numbers
 * `README.md`: update version numbers
 * `CHANGES.md`: summarize changes since last release

(Other changes may be necessary, especially for large releases.)

You can get a list of changes between release tags `v0.1.2` and `v0.2.0` via `git log v0.1.2..v0.2.0`. Scanning this list of commit messages is a good way to get a summary of what happened, although it does not account for conversations that occured on Github.

Once the relevant documentation changes have been committed, new [release notes](https://github.com/twitter/algebird/releases) should be added. You can add a release by clicking the "Draft a new release" button on that page, or if the relevant release already exists, you can click "Edit release".

The website should then be updated via `sbt docs/publishMicrosite`.

### License

By contributing your code, you agree to license your contribution under the terms of the [APLv2](LICENSE).
