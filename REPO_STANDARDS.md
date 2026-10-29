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
3. **Acceptance tests:** `None`, `Simple` or `Advanced`. See [Acceptance tests](#acceptance-tests).
4. **Maintainer(s),** with GitHub handles
5. **What it does,** with a screenshot or GIF where it helps
6. **Compatibility table:** Flame versions tested × OS (macOS, Rocky Linux). Only list what's actually been tested.
7. **Installation**
8. **Usage**
9. **Known issues**
10. **Credits and provenance:** where any adapted code came from, and its license
11. **License,** if the repo includes third-party libraries or uses model files. See [Licensing](#licensing).

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

## Licensing
The repo's own license is covered under [Required files](#required-files). This section covers everything else a tool uses at runtime.

### Model files
- **No repo may include model files.** Users download them after installing, either themselves or through the tool's code at runtime. That way responsibility for complying with a model's license rests with the user who downloads it, not with the repo's owners.
- If the tool downloads a model for the user, its interface must show the model's licenses, to the degree they can be established, covering the code, the weights and the training data, and record the user's acceptance, with a button or similar, before downloading. Where sources disagree, for example a model card and the model's original publication, say so rather than pick one. This is about the model's terms, not this tool's own license.

### License section in the README
Repos that include third-party libraries, or that use model files, must have a **License** section in the README. It lists every component used at runtime that has its own license, whether it's compiled in or downloaded, so users know up front what license terms come with using the tool.

The most important question for each component is whether it allows commercial use. Flame artists produce and modify commercial content, so their tools must not prohibit it.

A model has three parts that can carry different terms, so list them separately:
- the code or pipeline
- the weights
- the training data the weights were derived from

Label each component, and each part of a model, as `Commercial use allowed`, `Commercial use prohibited` or `Unknown`. For example:

| Component | Part | License | Commercial use |
|---|---|---|---|
| OpenCV | Library | Apache-2.0 | Allowed |
| ExampleNet | Code | MIT | Allowed |
| ExampleNet | Weights | CC BY-NC 4.0 | Prohibited |
| ExampleNet | Training data | Not stated | Unknown |

This information is here to help users decide. Everyone is responsible for making their own choices about the tools they use.

## Content that's never allowed
- Client media or confidential material, including in screenshots and sample files
- Autodesk-proprietary files or code
- Code whose license doesn't allow commercial use and redistribution. This includes many Shadertoy shaders (CC BY-NC-SA).
- Secrets, credentials or internal facility paths
- Large media files. Keep samples tiny, or link to them.
- Model files. See [Licensing](#licensing).

## Branches, merges and releases
- The default branch is `main`. It's protected: changes arrive by pull request with one approval, and force pushes and deletion are blocked.
- PRs are **squash-merged**, and merged branches are deleted automatically.
- Releases use **semantic versioning** (`v1.2.0`), are tagged on `main`, and are published as GitHub Releases with notes.

## Acceptance tests
Automated acceptance tests check that a new version still works as expected, and they reduce defects. We encourage them, but they're optional: each repo's maintainers decide whether to have them.

There are two classes:
- **Simple:** tests that can run on a GitHub-hosted runner.
- **Advanced:** tests that need special hardware or files, such as GPUs or large model files, so they can't run on a runner.

Each repo declares `None`, `Simple` or `Advanced` in its README.

| Level | How they run | Platforms | Effect on the release |
|---|---|---|---|
| None | No acceptance tests | — | Published as a normal release |
| Simple | Automatically, as part of the release build | One: Linux or macOS, whichever runner is available | The build only succeeds if the whole suite passes |
| Advanced | Offline, on maintainers' own machines | Every platform the release ships for | Published as a pre-release until the tests pass on every platform it ships for |

Simple tests only need one platform because they're less likely to depend on the hardware. Advanced tests need every platform the release ships for, because GPU and library support differ so much between macOS and Linux. A tool that ships for one platform only needs that one.

For a repo with advanced tests, the release build publishes the release as usual but marks it as a pre-release. Once the tests have been run offline and pass on every platform the release ships for, a maintainer notes the results in the release notes, including the OS and GPU each was run on, and removes the pre-release label.

We don't use self-hosted runners.

### Where the tests live
- Acceptance tests are part of the repo, so anyone can run them, not just maintainers.
- Put them in `tests/acceptance/`.
- Test data that's too large for the repo, such as model files, isn't committed. Instead, the repo has a script in `tests/acceptance/` that sets up the test data, including downloading any files. It puts the data in `tests/acceptance/data/`, which is listed in `.gitignore`, and the tests read it from there.
- The setup script has an option to use test data the tester already has. Given a local folder, it copies or links the files from there instead of downloading them again. For example, someone who already has the model files doesn't have to download them a second time.
- The README explains how to run the tests: the command, and any hardware or data they need.

### How they're written
- One command runs the whole suite and exits with a non-zero status if any test fails. That's what stops a release build when a simple test fails.
- Python tests use [pytest](https://docs.pytest.org/). C++ tests, including OpenFX plugins, follow the rules below. Other languages use their usual test tool, as long as the one-command rule holds.
- If a test's data or hardware is missing, it fails with a clear message. It doesn't skip, so a missing GPU or file can't look like a pass.

### C++ and OpenFX plugins
- Build with CMake, and register the tests with CTest so the suite runs with one command:
  ```bash
  cmake -B build && cmake --build build
  ctest --test-dir build --output-on-failure
  ```
  `ctest` exits with a non-zero status when any test fails. `--test-dir` needs CMake 3.20 or later.
- Write the tests with [GoogleTest](https://google.github.io/googletest/), and register them with `gtest_discover_tests()` from CMake's `GoogleTest` module, so each test shows up in CTest by name.
- Keep the image processing separate from the OpenFX glue code, so tests can run the processing directly without an OpenFX host.
- Run the GPU code paths on each platform's own GPU backend, such as Metal on macOS and CUDA on Linux. These are advanced tests.

### Testing in Flame
Every pull request should also be tested by hand in Flame, or in another OpenFX host for plugins. This isn't part of acceptance testing, because it isn't automated. Note what you tested in the PR's "How was it tested?" section: the Flame version, the OS and what you checked.

## Security
Dependabot alerts, secret scanning and private vulnerability reporting are on for every repo. See [SECURITY.md](SECURITY.md).
