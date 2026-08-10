# Contributing

Thank you for taking the time to contribute!

## Table of Contents

<!--ts-->
<!--te-->

## Code of Conduct
This project is governed by the [Code of Conduct](CODE_OF_CONDUCT.md)

## How To
### File a bug report

### Work on an issue

### Submit a pull request

#### Rebase merging
> [!NOTE]
> This section is intended for more advanced users.
> If you aren't comfortable with git, just stick to small pull requests and use squash merging.

If you need to submit a single pull request while still preserving history within the request, you can use rebase merging instead.
```console
$ git fetch
$ git rebase origin/main  # ensure you are up to date with the main branch
$ git rebase -i `git merge-base main HEAD`  # interactive rebase of all commits on the current branch since main
```
Then, use `pick` to select which commits you want to keep and `squash` to move changes to the previous `pick`ed commit.
You will then be given an opportunity to combine the commit messages of any squashed commits.
If you need to edit the messages any `pick`ed commits with no `squash`ed commits below them, use `reword` instead.
If you don't need to combine the commit messages of any `squash`ed commits (for example, if the commit is just a typo fix) use `fixup` instead.
It's also a good idea to add the line `exec just verify all` after every set of commits to ensure every individual commit passes all tests.

Once you've properly rebased your local branch, run `git log origin/main..HEAD --oneline` and check that the first lines follow [scoped commits](https://scopedcommits.com).
You should also run `git log origin/main..HEAD` and make sure the full commit messages include a detailed body.

## Styleguides
These conventions should be followed as much as possible, but none are absolutely set in stone.
If you feel a convention shouldn't apply to your work or you are confused on how to apply it, just make a note in your pull request and a maintainer will help.

### Pull requests
Pull request titles should follow [scoped commits](https://scopedcommits.com) for squash merging.
Related issues must be included like so: `scope(#1): description`, where `#1` is the issue number.

For rebase merging, use a descriptive title that starts with a capital letter and doesn't end with a period.

### Commits
We follow [scoped commits](https://scopedcommits.com).
Following the convention on individual branches is unnecessary, as typically pull requests will use the squash strategy.
Just make sure your pull request title follows the [Pull requests](#pull-requests) section.

If the rebase strategy is used, follow the [Rebase merging](#rebase-merging) section and make sure every remaining commit message follows [scoped commits](https://scopedcommits.com).

### Branch naming
We follow [conventional branch v1.0.0](https://conventionalbranch.org/v1.0.0).
We don't use v1.1.0 because we do not accept purely LLM-generated contributions.
Use the short versions of purpose prefixes (`feat/` and `fix/`).
If the branch is associated with an issue (it does not necessarily need to close the issue), include that in the branch name, for example: `feat/issue-1-add-some-feature`.

If multiple people are working on the same branch, they may also further scope branches with their names if they find it necessary.
For example, if Violet and Tyler are working together and want to keep their changes separate initially, they may use the branches `feat/issue-9-add-diff-drive-controller/violet` and `feat/issue-9-add-diff-drive-controller/tyler` respectively.
However, these branches should not be used for pull requests.
First, Violet and Tyler should merge their changes into `feat/issue-9-add-diff-drive-controller` then submit a pull request to merge `feat/issue-9-add-diff-drive-controller` into `main`.

### Markdown

## AI Agents
Purely LLM-generated pull requests are not accepted.
For now, no other hard rules are in place for LLM usage, but this is subject to change if we have problems with low quality pull requests.
If you are going to use AI, limit how much code it actually writes for you (especially in single blocks) and don't submit any code you don't understand and you should be fine.
