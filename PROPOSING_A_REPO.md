# Sharing a project

Built a tool, script, shader collection or plugin, or building one, that you'd like to host in the Logik org and develop *with* the community? Share it as a community project.

**This is for work that you, or someone you name, will maintain.** It doesn't have to be finished, but it does need an owner.

**Just have an idea** for a tool you'd like to exist? That goes in **Discussions → Ideas**. There's no form and no commitment, and someone may pick it up.

## 1. Check first
- Is there already a community repo that does this, or nearly does? Contributing there is usually better than starting fresh.
- Not sure it's ready? Post it in **Discussions → Ideas** to get feedback before sharing it here.

## 2. Share it
Go to [Discussions → Share a Project](https://github.com/orgs/flamelogik/discussions/categories/share-a-project) and click **New discussion**. The form asks for:
- the name and a short description
- what problem it solves for Flame artists
- the type (Python hook, Matchbox, OpenFX plugin, standalone tool, docs) and the area of Flame it's for
- supported Flame versions and operating systems
- the license (MIT by default)
- who will maintain it (usually you)
- the link, if the code already exists somewhere

## 3. Community comment (at least 7 days)
Anyone can comment, ask questions or offer to help. Owners may ask for changes.

## 4. Decision (within 14 days of the comment period closing)
An owner reviews the submission against these criteria:
- useful to Flame artists beyond one facility
- doesn't duplicate an existing community repo
- has a named maintainer
- uses an open-source license that allows commercial use (MIT preferred)
- has clear provenance, with no code of unknown origin or with non-commercial licensing
- contains no Autodesk-proprietary material, client media or secrets
- for compiled tools: includes the full source, and releases are built by GitHub Actions

Accepted submissions get the `accepted` label. Declined ones get `declined`, with an explanation of what (if anything) would change the answer.

## 5. After approval
- An owner creates the repo from the standard template and makes you its **maintainer**. You'll get an org invitation.
- If the code already lives in your personal GitHub account, it can be **transferred** into the org, keeping its history, stars and issues. The owner will walk you through it.
- Bring the repo up to the [repo standards](REPO_STANDARDS.md): README sections, license, changelog. The template gives you most of this.
- You work through pull requests like everyone else, and you review and merge PRs from other contributors.
