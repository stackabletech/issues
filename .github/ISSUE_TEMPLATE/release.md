---
name: Release Tracking
about: This template can be used to track the progress of the SDP
title: "chore(tracking): Release SDP XX.(X)X"
labels: ['epic']
assignees: ''

---

<!--
    DO NOT REMOVE THIS COMMENT. It is intended for people who might copy/paste from the previous release issue.
    This was created by an issue template: https://github.com/stackabletech/issues/issues/new/choose.
-->

# Stackable Release XX.(X)X

> [!IMPORTANT]
> Important dates:
> - ... - Release planning
> - ... - Lock product versions
> - ... - Target release date

## Release checklists

Replace the items in the task lists below with the applicable Pull Requests / Issues

### General Pre-Requisites (before Feature Freeze)

> [!TIP]
> These tasks should be done earlier in the process to lessen the burden at Pre-release time.

```[tasklist]
### Early Pre-release tasks
- [ ] Create a "Post XX.XX release" retro issue (does this need a template? See https://github.com/stackabletech/issues/issues/669)
- [ ] Define product versions to include in the next release
- [ ] [Update and release operator-rs workspace members](https://github.com/stackabletech/operator-rs/issues/new?template=release-workspace-members.md)
- [ ] [Update Rust toolchain of operators](https://github.com/stackabletech/operator-templating/issues/new?template=pre-release.md)
- [ ] [Update Rust dependencies of operators](https://github.com/stackabletech/issues/issues/new?template=pre-release-operator-rust-deps.md)
- [ ] [Update Container Images](https://github.com/stackabletech/docker-images/issues/new?template=early-pre-release.md)
```

> [!TIP]
> These tasks should be done a week or so before the release date.

```[tasklist]
### Pre-release
- [ ] Run all of the test suites in Jenkins (with all product versions, not just "nightly")
- [ ] [Check and update getting-started script](https://github.com/stackabletech/issues/issues/new?template=pre-release-getting-started-scripts.md)
- [ ] [Check and update demo charts](https://github.com/stackabletech/demos/issues/new?template=pre-release-chart-updates.md)
- [ ] [Test and update demos stable to nightly](https://github.com/stackabletech/demos/issues/new?template=pre-release-nightly-testing.md)
- [ ] Ensure integration tests are successful on OpenShift
- [ ] Check stackable-utils scripts in dry-run mode work
```

### Other Pre-Requisites (before Feature Freeze)

Search for open issues labeleded with [`scheduled-for/20XX-X`](https://github.com/search?q=org%3Astackabletech+label%3Ascheduled-for%2F20XX-X&type=issues&state=open)

```[tasklist]
### Other release-specific pre-requisites
- [ ] Run `niv update` and test via `make run-dev` (operator-templating)
```

### Feature freeze

This will not be so crucial with release branches, but is nonetheless sensible as it will make it easier to cherry-pick any release-related bugfixes from main into the release branch.

### End of the release cycle (Release day)

```[tasklist]
#### Technical tasks
- [ ] Temporarily remove branch protection before pushing the release branches/tags
- [ ] Create release branch for docker-images (see stackable-utils for script to create branches)
- [ ] Create release tag(s) for docker-images (see stackable-utils for scripts to create tags)
- [ ] Create release branches for operators (see stackable-utils for script to create branches)
- [ ] Create release tag(s) for operators (see stackable-utils for scripts to create tags)
- [ ] Create release tag for stackable-cockpit (optional, highly experimental, requires manual tag creation)
- [ ] Update release version in changelogs on main branches (see stackable-utils for script to do this)
- [ ] Create release branch for demos (see stackable-utils for script to create branches)
- [ ] Generate CRD docs [website](https://crds.stackable.tech/) for the new release by following these [instructions](https://github.com/stackabletech/crddocs)
- [ ] Test `stackablectl` with locally updated (to new release number) `releases.yaml`
- [ ] Update `release.yaml` in https://github.com/stackabletech/release/blob/main/releases.yaml
- [ ] ARM demo and integration testing of some kind
- [ ] [Check and update getting-started script](https://github.com/stackabletech/issues/issues/new?template=TODO-getting-started-scripts.md)
- [ ] [Test demos for the new release](https://github.com/stackabletech/demos/issues/new?template=TODO-release-testing.md)
- [ ] Check that an upgrade can be performed on an existing cluster without data loss (cycling demo)
- [ ] Run all of the test suites
- [ ] OpenShift testing on Rosa <!-- where is that at? -->
```

```[tasklist]
#### Documentation tasks
- [ ] Check the Changelog and/or issue labels to compile Release Highlights
- [ ] Compile list of new product versions that are supported and compile a list of new product features to include in the Release Highlights
- [ ] Upgrade guide: Document how to use stackablectl to uninstall all and install new release
- [ ] Upgrade guide: Document how to use helm to uninstall all and install new release
- [ ] Upgrade guide: Every breaking change of all our operators
- [ ] Upgrade guide: List dropped supported product versions (if there are some)
- [ ] Upgrade guide: List dropped supported operators (if there are some)
- [ ] Upgrade guide: List supported k8s versions
- [ ] The team reviews the preview release notes: (structure, wording, xrefs and links, sentences on new lines)
- [ ] Update SDP release version in documentation/modules/ROOT/pages/getting-started.adoc and test the release install command
- [ ] Cut a release branch (see [scripts/make-release-branch.sh](https://github.com/stackabletech/documentation/blob/main/scripts/make-release-branch.sh))
- [ ] Update releases in the playbook (see [scripts/publish-new-version.sh](https://github.com/stackabletech/documentation/blob/main/scripts/publish-new-version.sh))
- [ ] Update antora.yaml version in stackabletech/demos on the release branch - the stackable-utils release-scripts should do this like they do for products and operators.
- [ ] Set the release to "Released" in the Feature Tracker and create a new release (how?)
- [ ] Update the getting-started page in the main docs and check it works with this release: https://github.com/stackabletech/documentation/blob/main/modules/ROOT/pages/getting-started.adoc
```

Marketing tasks can now reference published documentation.

```[tasklist]
#### Marketing tasks
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
- [ ] Post an announcement via OSBA (Ping Lars, info@osb-alliance.com)
- [ ] Send announcement to Kubernetes Podcast (Ping Lars)
- [ ] Send announcement to Heiser
- [ ] Ping the stackable-ionos-tech channel or anyone responsible once all tags are created
```

```[tasklist]
### Post-release tasks
- [ ] Update the list of supported SDP releases in Jira (ping Jim)
- [ ] Openshift certification. Create an issue from this [template](https://github.com/stackabletech/issues/blob/main/.github/ISSUE_TEMPLATE/olm_manifests.md) for the OLM manifests
- [ ] Mark any releases older than one year as "end-of-life" [in the documentation](https://github.com/stackabletech/documentation/blob/f751e7ff7cddacae7d2c6c2c6c1d1c877c7aa11c/antora.yml#L18) How? Ask Lars of course. He's good at that stuff.
- [ ] Post XX.XX release retro (use issue created at the start of the process)
- [ ] [Create the next release tracking task](https://github.com/stackabletech/issues/issues/new?template=release.md) (if the date is available)
```
