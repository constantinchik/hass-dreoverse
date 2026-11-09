# Contribution guidelines

Contributing to this project should be as easy and transparent as possible, whether it's:

- Reporting a bug
- Discussing the current state of the code
- Submitting a fix
- Proposing new features

## Github is used for everything

Github is used to host code, to track issues and feature requests, as well as accept pull requests.

Pull requests are the best way to propose changes to the codebase.

1. Fork the repo and create a focused branch from the target repository's verified
   published default branch (`master` for this fork). Inspect current remote refs
   and open PRs first; preserve existing work in other branches and dirty trees.
2. If you've changed something, update the documentation.
3. Run the applicable offline checks below.
4. Report validation evidence and any checks not run.
5. Issue that pull request!

## Any contributions you make will be under the MIT Software License

In short, when you submit code changes, your submissions are understood to be under the same [MIT License](http://choosealicense.com/licenses/mit/) that covers the project. Feel free to contact the maintainers if that's a concern.

## Report bugs using Github's [issues](../../issues)

GitHub issues are used to track public bugs.
Report a bug by [opening a new issue](../../issues/new/choose); it's that easy!

## Write bug reports with detail, background, and sample code

**Great Bug Reports** tend to have:

- A quick summary and/or background
- Steps to reproduce
  - Be specific!
  - Give sample code if you can.
- What you expected would happen
- What actually happens
- Notes (possibly including why you think this might be happening, or stuff you tried that didn't work)

People *love* thorough bug reports. I'm not even kidding.

## Offline checks and formatting

Run from the repository root. The [lint workflow](.github/workflows/lint.yml)
uses Python 3.12 and Ruff from [requirements.txt](requirements.txt). If setting
up a development environment is in scope, install that tooling with
`python3 -m pip install -r requirements.txt`.

With the tooling already installed, these are the nonmutating CI checks:

```sh
python3 -m ruff check .
python3 -m ruff format . --check
```

Ruff follows [.ruff.toml](.ruff.toml). [scripts/lint](scripts/lint) is a mutating
convenience command: it runs `ruff format .` and `ruff check . --fix`. Review its
diff and keep unrelated formatting or fixes out of the PR.

There is currently no dedicated automated test suite in this checkout. For a
documentation-only change, check links and required files against the proposed
Git tree, run `git diff --check`, and review the changed paths. Report unavailable
tooling explicitly; do not provision or start Home Assistant just to validate docs.

## Model support and validation evidence

Keep changes isolated by device or feature. PRs should identify exact model
numbers, affected entity platforms, related issues, and the evidence for each
claimed behavior. Update the [README](README.md) when supported models or behavior
change. Keep manifest/release changes and unrelated cleanup out of feature PRs
unless they are explicitly part of the release scope.

Distinguish these evidence levels in PRs and support documentation:

- **Offline:** source inspection, static checks, or fixtures. A model mapping or
  shared protocol suggests support but does not prove behavior on another model.
- **Live integration:** discovery, entity creation, state updates, and reported
  control results observed in an approved Home Assistant/account session.
- **Physical:** the actual device's response observed for the specific model and
  feature. A successful API call alone does not establish this.

Label inferred features and untested platforms explicitly. Preserve existing
model/platform evidence when documenting support; do not generalize a verified
feature to every model or variant. State what was not tested.

## Approval boundaries

Repository edits and PR publication do not authorize merging, deployment, service
changes, account access, or device controls. Obtain separate explicit approval
for the applicable live or physical work and keep private installation details,
credentials, account/device identifiers, and raw private state out of commits.

[scripts/develop](scripts/develop) may install Home Assistant, initialize local
configuration, and start an instance. Use it only within an approved runtime
validation scope; real account login and device controls also need that scope.
Live or physical acceptance is conditional on that approval, not an automatic
prerequisite for a documentation PR.

## License

By contributing, you agree that your contributions will be licensed under its MIT License.
