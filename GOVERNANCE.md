# Governance

This explains how the Logik GitHub organization is run, who can do what, and how decisions get made. Logik is a volunteer community, so these rules aim to be light and clear.

## Roles

### Contributors: anyone
Anyone with a GitHub account can open issues, join Discussions, propose new repos and submit pull requests. You don't need to be an org member to contribute. Fork the repo and open a PR.

### Maintainers
A maintainer looks after one or more specific repos. Maintainers have the **Maintain** role on their repos, through a per-repo team (`@flamelogik/REPO-maintainers`). Maintainers can:
- review and merge pull requests
- triage, label and close issues
- cut releases

Maintainers **cannot** delete repos, change a repo's visibility, change branch protection, or create new repos.

A maintainer is expected to:
- respond to new issues and PRs, aiming for within two weeks (volunteer pace is fine, but silence isn't)
- keep the README's compatibility table and status line honest
- say so when they need a break or want to step down

### Owners
Owners administer the organization: settings, membership, teams, creating repos, and enforcing the code of conduct. Owners don't control the content of repos they don't maintain.

## How decisions are made

Owner approval (🔑) is needed for these decisions:
- accepting a new repo proposal
- adding or removing a maintainer
- archiving a repo
- changing this document, the code of conduct or other org-wide policies
- granting any exception to the [repo standards](REPO_STANDARDS.md)

**Current rule (interim):** approval from **one owner** is enough. Two of the three current owners are inactive, and this keeps the org moving. While only one owner is active, that owner can also merge their own pull requests to the infrastructure repos without a second review, since there is nobody else to review them. This ends with the switch below.

**Planned rule:** once the org has **at least two active owners**, 🔑 decisions need approval from **2 of 3 owners**. An owner counts as active when they have responded to an owner request within the last 90 days. The switch is recorded in the [decision log](https://github.com/flamelogik/org-handbook/blob/main/DECISIONS.md).

Day-to-day decisions within a repo (which PRs to merge, what the roadmap is) belong to that repo's maintainers.

Significant decisions are recorded, with dates and reasons, in the [decision log](https://github.com/flamelogik/org-handbook/blob/main/DECISIONS.md).

## Independently run projects

**LogikProjekt** (the `LOGIK-PROJEKT` and `PROJEKT-DEVELOPMENT` repos) is run by its maintainer independently of the rest of the org. The rules, templates, standards and approval process described here don't apply to it, except for the few settings GitHub enforces across the whole organization (such as required 2FA).

## Becoming a maintainer

- **For a new repo:** the person who proposes a repo becomes its first maintainer once the proposal is approved.
- **For an existing repo:** you're a good candidate when you've built a track record in that repo, usually 3 or more merged PRs or consistent, helpful issue triage. A current maintainer or an owner nominates you, or you can ask. An owner approves.

Maintainer access is reviewed **once a year**. Maintainers inactive for 12 months get a friendly check-in. If they don't reply, they move to emeritus status and are credited in the README's Credits section. Coming back later is welcome.

## Owner changes

- New owners are added by owner approval (🔑). They should be active, trusted members of the Logik community.
- The org should always have **at least two** owners, so it's never locked out.
- An owner inactive for 6 months will be asked whether they want to stay on. Nobody is removed as owner without their agreement unless they've been unreachable for 12 months.

## Archiving

A repo may be archived (🔑) when it has had no maintainer for 6 months and a public call for maintainers has gone unanswered for 30 days, or when it no longer works with any supported Flame version. Archived repos stay readable and forkable, and can be revived. **Community repos are never deleted.**

## Changing this document

Open a pull request against this file. Significant changes stay open for at least 7 days for community comment before an owner merges them.
