# Contributing

**Table of Contents**

- [Newcomers](#newcomers)
- [Our engineering standards](#our-engineering-standards)
- [Source code contribution](#source-code-contribution)
- [IDE Configuration](#ide-configuration)
- [Run locally](#run-locally)
- [FAQ](#frequently-asked-questions)

**Never report security issues on GitHub, public issues or other public channels (Discord etc.). Follow the instructions in the [SECURITY.md](https://github.com/OneLiteFeatherNET/.github/blob/main/SECURITY.md) to report vulnerabilities privately.**

We appreciate any kind of contributions: code, documentation, design, etc. Any contribution counts, and the size does not matter!

## Newcomers

If you are a newcomer contributor, look for the label `Good first issue`. Issues labeled like that can be resolved without having in-depth knowledge about the codebase you are contributing to.

## Our engineering standards

OneLiteFeather repositories follow a small set of shared standards so build, release and maintenance work the same way everywhere. Please align your contribution with them:

- **Conventional Commits** — commit messages (and, on squash-merge, the PR title) follow the [Conventional Commits](https://www.conventionalcommits.org/) spec (`feat:`, `fix:`, `chore:`, …). They drive automated versioning and changelogs: a `feat:` bumps the minor version, `fix:` the patch version, and a breaking change (`feat!:` or a `BREAKING CHANGE:` footer) the major version.
- **Trunk-based branches** — branch off the default branch with a type prefix (`feat/`, `fix/`, `chore/`, `refactor/`, `hotfix/`). Changes reach the default branch only via pull request, merged as a **squash merge**.
- **Automated releases** — releases are produced by [release-please](https://github.com/googleapis/release-please); do not tag or bump versions by hand.
- **Central CI/CD** — pipelines reuse the shared workflows in [`OneLiteFeatherNET/workflows`](https://github.com/OneLiteFeatherNET/workflows) (build, publish, docker, lint) rather than repo-local copies.
- **Dependency updates** — dependencies are managed via the shared Renovate preset in [`OneLiteFeatherNET/renovate`](https://github.com/OneLiteFeatherNET/renovate).

[`Cygnus`](https://github.com/OneLiteFeatherNET/Cygnus) is the reference implementation of this setup.

## Source code contribution

- For larger contributions, create an issue for any required discussion first.
- Implement the solution on a branch in your fork that is **not the default branch**.
- Once you're done, create a pull request. GitHub will request a review from a maintainer automatically.
    - Title your pull request as a Conventional Commit — it is used for the squash-commit message and release notes.
    - Please raise one PR per issue or enhancement. The smaller the change, the easier and faster the review. We don't mind receiving several small PRs.

### IDE Configuration

If a project has a code style policy, you can find an `.editorconfig` file in the root directory of the project. If you're using IntelliJ, install the `EditorConfig` plugin. Writing or reformatting files then follows our standards.

### Run locally

To get started, you will need the following software, most of which can be obtained via common package managers such as `apt` (Debian / Ubuntu), `homebrew` (macOS / Linux), and more:

- `git` (package `git` everywhere)
- A **Java 25 or later** JDK (packages vary).
    - [Adoptium](https://adoptium.net/) has builds for most operating systems.
    - If not stated otherwise, our projects use Gradle's [Toolchain](https://docs.gradle.org/current/userguide/toolchains.html) feature, so Gradle will automatically provision the required JDK for compilation if it cannot find an existing install.

If you are on Windows, you can download git [here](https://git-scm.com/downloads). The instructions for Java apply nevertheless.

Compiling is done by invoking `build` (add `clean` when needed) with the project's build tool.

## Frequently Asked Questions

### My commit doesn't need a build, what do I do?

Quite simple: add `[ci skip]` to the start of your commit subject.

This most often applies to changes to files like `README.md`, this very file (`CONTRIBUTING.md`), the `LICENSE` file, and so forth.
