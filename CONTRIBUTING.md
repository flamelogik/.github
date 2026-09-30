# Contributing to Logik community projects

Thanks for helping. These tools exist because Flame artists share what they build. You don't need to be a developer, or even a GitHub expert, to contribute.

## Ways to help

- **Report bugs** using the bug report form in the tool's repo. The Flame version and OS details really matter.
- **Improve documentation.** Clearer install steps, screenshots and "gotchas" help everyone.
- **Test** a tool on a Flame version or OS that's missing from its compatibility table, and report back.
- **Fix bugs or add features** through a pull request.
- **Answer questions** in [Discussions → Q&A](https://github.com/orgs/flamelogik/discussions).
- **Propose a new tool** for the community. See [Proposing a new repo](PROPOSING_A_REPO.md).

## How contributions work

Nobody pushes directly to community repos, not even owners. Every change arrives as a **pull request (PR)** and is reviewed before it's merged. You don't need to be an org member: you work in your own copy (a *fork*) and send changes back.

### First time? The whole flow with the GitHub CLI

```bash
# One-time setup (macOS: brew; Rocky Linux: dnf)
brew install gh          # or: sudo dnf install gh
gh auth login

# 1. Fork the repo and clone your fork
gh repo fork flamelogik/REPO --clone
cd REPO

# 2. Create a branch for your change
git switch -c fix-timeline-crash

# 3. Make your changes, test them in Flame, then commit
git add -A
git commit -m "Fix crash when timeline has no segments"

# 4. Push and open the pull request
git push -u origin fix-timeline-crash
gh pr create --fill
```

You can also do all of this in the GitHub website: click **Fork**, edit files in the browser, and GitHub offers to open a PR.

### Before you start something big

For anything bigger than a small fix, **open an issue first** to describe what you want to do. The maintainer might already be working on it, or have context that saves you time.

## What makes a good pull request

- **One change per PR.** A bug fix and a new feature are two PRs.
- **Explain what and why** in the description. Screenshots or a short screen recording help a lot for UI changes.
- **Say what you tested:** which Flame version(s) and which OS. The PR template asks for this.
- **Update docs and the CHANGELOG** if behavior changes.
- **Expect review feedback.** It's part of the process, not a judgment. Maintainers are volunteers, so allow a week or two for a response.

## What we can't accept

To keep these tools safe and legal for commercial facilities:

- **No compiled binaries** in commits (`.so`, `.dylib`, `.ofx` bundles, executables). Compiled tools are built from source by GitHub Actions and published as Releases. See the [repo standards](REPO_STANDARDS.md).
- **No client media or confidential material,** including in screenshots and test files.
- **No Autodesk-proprietary files** or code you don't have the right to share.
- **No code of unknown origin.** If you ported or adapted code (a Shadertoy shader, a snippet from a forum), say where it came from in the PR, and make sure its license allows commercial use and redistribution. Many Shadertoy shaders use a *non-commercial* license, which we can't accept.
- **No secrets:** API keys, passwords, internal server paths.

## AI-assisted code

Using AI tools is fine. You're responsible for what you submit: understand it, test it in Flame, and make sure it doesn't reproduce code under an incompatible license.

## Licensing of contributions

By submitting a pull request, you agree that your contribution is licensed under that repo's license (MIT for most community repos). You also confirm that you have the right to submit it.

## Becoming a maintainer

Regular, helpful contributors are invited to become maintainers. See [Governance](GOVERNANCE.md#becoming-a-maintainer).

## Code of conduct

Everyone taking part is expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md).
