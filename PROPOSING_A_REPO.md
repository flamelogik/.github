# Proposing a new repo

Have a tool, script, shader collection or plugin you'd like to develop *with* the community? Propose it as a community repo.

## 1. Check first
- Is there already a community repo that does this, or nearly does? Contributing there is usually better than starting fresh.
- Still rough? Post it in **Discussions → Ideas** to get feedback before writing a full proposal.

## 2. Submit the proposal
Go to [Discussions → Repo Proposals](https://github.com/orgs/flamelogik/discussions/categories/repo-proposals) and click **New discussion**. The form asks for:
- the name and a short description
- what problem it solves for Flame artists
- the type (Python hook, Matchbox, OpenFX plugin, standalone tool, docs)
- supported Flame versions and operating systems
- the license (MIT by default)
- who will maintain it (usually you)
- the link, if the code already exists somewhere

## 3. Community comment (at least 7 days)
Anyone can comment, ask questions or offer to help. Owners may ask for changes.

## 4. Decision (within 14 days of the comment period closing)
An owner reviews the proposal against these criteria:
- useful to Flame artists beyond one facility
- doesn't duplicate an existing community repo
- has a named maintainer
- uses an open-source license that allows commercial use (MIT preferred)
- has clear provenance, with no code of unknown origin or with non-commercial licensing
- contains no Autodesk-proprietary material, client media or secrets
- for compiled tools: includes the full source, and releases are built by GitHub Actions

Accepted proposals get the `accepted` label. Declined ones get `declined`, with an explanation of what (if anything) would change the answer.

## 5. After approval
- An owner creates the repo from the standard template and makes you its **maintainer**. You'll get an org invitation.
- If the code already lives in your personal GitHub account, it can be **transferred** into the org, keeping its history, stars and issues. The owner will walk you through it.
- Bring the repo up to the [repo standards](REPO_STANDARDS.md): README sections, license, changelog. The template gives you most of this.
- You work through pull requests like everyone else, and you review and merge PRs from other contributors.
