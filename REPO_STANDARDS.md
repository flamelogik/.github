# Repo Standards

Every community repo (all repos except LogikProjekt, which is independently run) follows these standards. Artists in commercial facilities rely on these tools, so consistency and trust matter.

## Required files

| File | Notes |
|---|---|
| `README.md` | Uses the template's sections (see below) |
| `LICENSE` | MIT by default. Other licenses need owner approval and must be OSI-approved and allow commercial use. |
| `CHANGELOG.md` | Newest first. Update it with every release. |
| `.github/CODEOWNERS` | `* @flamelogik/REPO-maintainers` |

The contributing guide, code of conduct, security policy, and issue and PR templates are inherited from the org's `.github` repo automatically. Don't copy them in unless a repo truly needs its own version.

## README sections
1. **Name and one-line description**
2. **Status line:** `Maintained`, `Seeking maintainer` or `Archived (reason, date)`
3. **Maintainer(s),** with GitHub handles
4. **What it does,** with a screenshot or GIF where it helps
5. **Compatibility table:** Flame versions tested × OS (macOS, Rocky Linux). Only list what's actually been tested.
6. **Installation**
7. **Usage**
8. **Known issues**
9. **Credits and provenance:** where any adapted code came from, and its license

## Naming and topics
- Repo names are **lowercase-with-hyphens** and describe the tool, e.g. `batch-render-tools`, `matchbox-film-grain`.
- Tag every repo with `flame` and `logik`, plus topics on two axes: at least one **kind** topic (what it is) and at least one **area** topic (what it's for). A repo can have several of each.

**Kind topics**

| Topic | For |
|---|---|
| `flame-python` | Python hooks and scripts |
| `matchbox` | Matchbox shaders |
| `openfx` | OpenFX plugins |
| `flame-tool` | Standalone apps and utilities |
| `documentation` | Guides and reference material |

**Area topics**

| Topic | For |
|---|---|
| `flame-timeline` | Timeline and sequence work: segments, markers, versions, transitions |
| `flame-batch` | Batch and BFX setups, node tools, setup management |
| `flame-color` | Grading, LUTs, colour management |
| `flame-tracking` | Tracking, stabilisation, planar and camera tracking |
| `flame-keying` | Keying, mattes, compositing helpers |
| `flame-conform` | Conform, import and export, EDL/AAF/XML, media management |
| `flame-openclip` | Open Clip creation, versioning and relinking |
| `flame-publish` | Publishing shots and renders to other tools and pipelines (ShotGrid/Flow, ftrack, Nuke, After Effects) |
| `flame-pipeline` | Render, Burn and farm jobs, project setup, naming and delivery |
| `flame-ui` | Menus, shortcuts, panels and general workflow helpers |

Topics are searchable, so an artist can find every timeline tool with `org:flamelogik topic:flame-timeline`, or every Matchbox for keying with both topics. If nothing fits, propose a new area topic in a PR to this file rather than inventing one per repo.

## Flame version compatibility
Flame's bundled Python and Qt change between releases. The move from PySide2 to PySide6, for example, broke many scripts. Keep the compatibility table current. When dropping support for an old Flame version, note it in the CHANGELOG.

## Compiled tools: OpenFX plugins and apps
- **The full source code lives in the repo.**
- **Never commit binaries.** Releases are built by GitHub Actions from a tagged commit and attached to a GitHub Release, so anyone can check that a download matches the public source.
- Build instructions in the README must let someone reproduce the build.
- Where possible, macOS builds should be signed and notarized. Say so in the README if they aren't.

## Content that's never allowed
- Client media or confidential material, including in screenshots and sample files
- Autodesk-proprietary files or code
- Code whose license doesn't allow commercial use and redistribution. This includes many Shadertoy shaders (CC BY-NC-SA).
- Secrets, credentials or internal facility paths
- Large media files. Keep samples tiny, or link to them.

## Branches, merges and releases
- The default branch is `main`. It's protected: changes arrive by pull request with one approval, and force pushes and deletion are blocked.
- PRs are **squash-merged**, and merged branches are deleted automatically.
- Releases use **semantic versioning** (`v1.2.0`), are tagged on `main`, and are published as GitHub Releases with notes.

## Security
Dependabot alerts, secret scanning and private vulnerability reporting are on for every repo. See [SECURITY.md](SECURITY.md).
