---
name: Release Tracking
about: This template can be used to track the progress of the SDP
title: "chore(tracking): SDP Release YY.M.X"
labels: ['epic']
assignees: ''
---

<!--
    DO NOT REMOVE THIS COMMENT. It is intended for people who might copy/paste from the previous release issue.
    This was created by an issue template: https://github.com/stackabletech/issues/issues/new/choose.
-->

> [!IMPORTANT]
> Important dates:
>
> - ... - Release planning
> - ... - Lock product versions
> - ... - Final operator-rs release at CoB
> - ... - Begin bumping operator-rs crates in each operator
> - ... - Begin release-branching tasks
> - ... - Target release date (marketable)

> [!TIP]
> Replace the items in the task lists below with the applicable Pull Requests / Issues.

## Early Pre-release tasks

> [!TIP]
> These tasks should be done earlier in the process to lessen the burden at Pre-release time.

- [ ] [Create release and release-retro labels][epr-1] if not already present
- [ ] [Create a "Release Retro" issue][epr-2]
- [ ] Define product versions to include in the next release
- [ ] [Major or Minor Container Images updates][epr-3]
- [ ] [Patch Container Images updates][epr-3] (Do not reuse the previous issue)

[epr-1]: https://github.com/stackabletech/infrastructure/blob/main/label_sync/labels.yml
[epr-2]: https://github.com/stackabletech/issues/issues/new?template=08-release-retro.md
[epr-3]: https://github.com/stackabletech/docker-images/issues/new?template=early-pre-release.md

## Pre-release

> [!TIP]
> These tasks should be done a week or so before the release date.

- [ ] [Update and release operator-rs workspace members][pr-1]
- [ ] [Update Rust toolchain of operators][pr-2]
- [ ] [Update Rust dependencies of operators][pr-3]
- [ ] Run all of the test suites in Jenkins (with all product versions, not just "nightly")
- [ ] [Check and update getting-started scripts][pr-4]
- [ ] [Check and update demo charts][pr-5]
- [ ] [Test demo upgrades (stable to nightly)][pr-6]
- [ ] [Test demos from scratch (nightly)][pr-7]
- [ ] Ensure integration tests are successful on OpenShift (run with `--test-suite openshift` against Replicated OKD)
- [ ] Check [stackable-utils] scripts in dry-run mode work
- [ ] Search for open issues labeled with [scheduled-for/YY.M.X][pr-8]

[pr-1]: https://github.com/stackabletech/operator-rs/issues/new?template=release-workspace-members.md
[pr-2]: https://github.com/stackabletech/operator-templating/issues/new?template=pre-release.md
[pr-3]: https://github.com/stackabletech/issues/issues/new?template=05-pre-release-operator-rust-deps.md
[pr-4]: https://github.com/stackabletech/issues/issues/new?template=03-pre-release-getting-started-scripts.md
[pr-5]: https://github.com/stackabletech/demos/issues/new?template=pre-release-chart-updates.md
[pr-6]: https://github.com/stackabletech/demos/issues/new?template=pre-release-upgrade-testing.md
[pr-7]: https://github.com/stackabletech/demos/issues/new?template=pre-release-from-scratch-testing.md
[pr-8]: https://github.com/search?q=org%3Astackabletech+label%3Ascheduled-for%2FYY.M.X&type=issues&state=open

## Release branching

> [!CAUTION]
> A small change freeze is required until these tasks have been completed.

> [!TIP]
> See [stackable-utils] for script to create tags and update changelogs.

- [ ] Create release branch for docker-images
- [ ] Create release branches for operators
- [ ] Create release branch for demos
- [ ] _Wait for images to be built before proceeding_

## Release candidate testing

> [!WARNING]
> To be discussed during the on-site.
>
> Getting started scripts use particular product versions (this would have been updated in the
> early-pre-release stage), however, at this point in time, the images will be tagged with an rcX
> tag.

<!--

> [!TIP]
> As issues are discovered, they can be fixed on the `main` branch, and cherry-picked into the release branch.
>
> Please ensure the changelog is updated and correct for the release after cherry-picking changes.
> Please also keep PR links as they are in `main` (do not update them for the cherry-picked PR).

- [ ] [Check and update getting-started scripts](https://github.com/stackabletech/issues/issues/new?template=07-release-getting-started-scripts.md) for the Release Candidate
- [ ] [Test demos and upgrade from previous to this release](https://github.com/stackabletech/demos/issues/new?template=release-upgrade-testing.md) for Release Candidate (only fresh install)

-->

## Release tagging

> [!TIP]
> See [stackable-utils] for script to create tags and update changelogs.

- [ ] Create release tag(s) for docker-images
- [ ] Create release tag(s) for operators
- [ ] Update release version in changelogs on main branches
- [ ] _Wait for images to be built before proceeding_
- [ ] Test `stackablectl` with locally updated (to new release number) `releases.yaml`
- [ ] Update [release.yaml](https://github.com/stackabletech/release/blob/main/releases.yaml)
- [ ] Release stackablectl

## Release verification

> [!TIP]
> These tasks do not block the Documentation tasks below and can be done concurrently.

- [ ] [Check getting-started scripts][rv-1]
- [ ] [Test demos from scratch (YY.M.X)][rv-2]
- [ ] Check that an upgrade can be performed on an existing cluster without data loss (cycling demo)
- [ ] Run all integration tests (for both `x86_64` and ~`aarch64`~ (defer aarch64 until interu is used))
- [ ] Ensure integration tests are successful on OpenShift (run with `--test-suite openshift` against Replicated OKD)

[rv-1]: https://github.com/stackabletech/issues/issues/new?template=07-release-getting-started-scripts.md
[rv-2]: https://github.com/stackabletech/demos/issues/new?template=release-from-scratch-testing.md

## Documentation tasks

> [!TIP]
> Name the release-notes branch `docs/release-notes-YY.M.X` so that the link below takes you directly to the [Pull Request template][docs-pr-template].

- [ ] Generate CRD docs [website][dt-1] for the new release by following these [instructions][dt-2]
- [ ] Create a stackabletech/documentation branch called `docs/release-notes-YY.M.X`
- [ ] Compile list of new product features in newly supported versions for the YY.M.X release (for the blog post)
- [ ] Begin writing the release notes with the [Pull Request template][dt-3]
- [ ] Update SDP release version in `documentation/modules/ROOT/pages/getting-started.adoc` and test the release install command
- [ ] Cut a release branch (see [scripts/make-release-branch.sh][dt-4])
- [ ] Update releases in the playbook (see [scripts/publish-new-version.sh][dt-5])
- [ ] Remove any references to HEAD and main from the Antora playbooks on the release branch (replace with the release branch)
- [ ] Update antora.yaml version in stackabletech/demos on the release branch - the stackable-utils release-scripts should do this like they do for products and operators.
- [ ] Set the release to "Released" in the Feature Tracker and create a new release (ping @lfrancke)
- [ ] Update the [getting-started page][dt-6] in the main docs and check it works with this release

[dt-1]: https://crds.stackable.tech/
[dt-2]: https://github.com/stackabletech/crddocs
[dt-3]: https://github.com/stackabletech/documentation/compare/main...docs/release-notes-YY.M.X?template=release-notes.md&title=chore(tracking):%20Release%20Notes%20for%20SDP%20YY.M.X
[dt-4]: https://github.com/stackabletech/documentation/blob/main/scripts/make-release-branch.sh
[dt-5]: https://github.com/stackabletech/documentation/blob/main/scripts/publish-new-version.sh
[dt-6]: https://github.com/stackabletech/documentation/blob/main/modules/ROOT/pages/getting-started.adoc
[docs-pr-template]: https://github.com/stackabletech/documentation/tree/main/.github/PULL_REQUEST_TEMPLATE/release-notes.md&title=chore(tracking):%20Release%20Notes%20for%20SDP%20YY.M.X

## Marketing tasks

> [!NOTE]
> Marketing material can now reference published documentation.

- [ ] Write marketing / customer oriented release summary to be published in the marketing channels
- [ ] Update the homepage banner (as long as we have it) to point to the new release
- [ ] Write a blogpost / news article announcing the new release (optional)
- [ ] Write a description of new demos for homepage/demos section
- [ ] Announce Release on LinkedIn
- [ ] Announce Release in Newsletter (optional)
- [ ] Produce a release highlight video (optional)
- [ ] Announce Release on Hacker News (optional)
- [ ] Post an announcement in the GitHub [Discussions Announcement forum](https://github.com/stackabletech/community/discussions/categories/announcements) and make it a pinned discussion while at the same time removing the old pinned thread
- [ ] Post an announcement in Discord
- [ ] Post an announcement on DOK Community in the #be-shameless Channel (Ping Lars or Jim)
- [ ] Post an announcement via OSBA (Ping Lars, <mailto:info@osb-alliance.com>)
- [ ] Send announcement to Kubernetes Podcast (Ping Lars)
- [ ] Send announcement to Heiser
- [ ] Ping the stackable-ionos-tech channel or anyone responsible once all tags are created

## Post-release tasks

- [ ] Test demo upgrades, which were skipped in the previous testing (optional)
- [ ] Update the list of supported SDP releases in Jira (ping @Jimvin)
- [ ] Openshift certification. [Create an issue][pt-1] to track the creation of the OLM manifests
- [ ] Mark any releases older than one year as "end-of-life" in the documentation (update [antora.yaml][pt-2] on the applicable branches).
- [ ] _Link to release retro issue (use issue created at the start of the process)_
- [ ] Update the release tracking templates (optional)
- [ ] [Create the next release tracking task][pt-3] (if the date is available)

[pt-1]: https://github.com/stackabletech/issues/issues/new?template=09-olm_manifests.md
[pt-2]: https://github.com/stackabletech/documentation/blob/f751e7ff7cddacae7d2c6c2c6c1d1c877c7aa11c/antora.yml#L18
[pt-3]: https://github.com/stackabletech/issues/issues/new?template=06-release.md
[stackable-utils]: https://github.com/stackabletech/stackable-utils/blob/main/release/README.md
