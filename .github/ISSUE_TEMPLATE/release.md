---
name: Release
about: This template can be used to track the release process at Stackable
title: Release XX.(X)X
labels: ''
assignees: ''

---

# Stackable Release XX.(X)X

## Release checklists

```[tasklist]
### General pre-requisites (before feature freeze)
- [ ] Bump operator-rs to latest version in all operators. This should be done early in the release cycle to leave sufficient time for testing etc.
- [ ] Check Rust and e.g. cargo deps versions
- [ ] Run/check getting-started scripts
- [ ] Run/check demos with dev release and main branch and create draft PR for release-related changes
```

```[tasklist]
### Other release-specific pre-requisites
- [ ] ...
```

### Feature freeze

This will not be so crucial with release branches, but is nonetheless sensible as it will make it easier to cherry-pick any release-related bugfixes from main into the release branch.

### End of the release cycle (Release day)

```[tasklist]
#### Technical tasks
- [ ] Create release branches for docker-images (see stackable-utils for script to create branches)
- [ ] Create release tag(s) for docker-images (see stackable-utils for scripts to create tags)
- [ ] Create release branches for operators (see stackable-utils for script to create branches)
- [ ] Create release tag(s) for operators (see stackable-utils for scripts to create tags)
- [ ] Update changelogs in main branches (see stackable-utils for script to do this)
- [ ] Check integration tests (use a table in Nuclino - easier for concurrent editing)
- [ ] Check getting started scripts (use a table in Nuclino)
- [ ] Check (new) stackablectl Stacks and Demos (use a table in Nuclino)
- [ ] Test with locally updated (to new release number) `releases.yaml`
- [ ] Update `release.yaml` in https://github.com/stackabletech/release/blob/main/releases.yaml
- [ ] Check that an upgrade can be performed on an existing cluster without data loss.
```
```[tasklist]
#### Documentation tasks
- [ ] Check the Changelog and/or issue labels to compile Release Highlights
- [ ] Upgrade guide: Document how to use stackablectl to uninstall all and install new release
- [ ] Upgrade guide: Document how to use helm to uninstall all and install new release
- [ ] Upgrade guide: Every breaking change of all our operators
- [ ] Upgrade guide: List dropped supported product versions (if there are some)
- [ ] Upgrade guide: List dropped supported operators (if there are some)
- [ ] Upgrade guide: List supported k8s versions
- [ ] Update version of main documentation repo
- [ ] Set the release to "Released" in the Feature Tracker and create a new release
- [ ] Add documentation note (release notes): when we change the default pvc size, the user needs to delete the sts, as we are not allowed to change the pvc in sts spec
- [ ] Update the getting-started page in the main docs and check it works with this release: https://github.com/stackabletech/documentation/blob/main/modules/ROOT/pages/getting_started.adoc
```

Marketing tasks can now reference published documentation.

```[tasklist]
#### Marketing tasks
- [ ] Write marketing / customer oriented release summary to be published in the marketing channels
- [ ] Update the homepage banner (as long as we have it) to point to the new release
- [ ] Write a blogpost / news article announcing the new release (optional)
- [ ] Write a description of new demos for hmepage/demos section
- [ ] Announce Release on linkedIn
- [ ] Announce Release on Twitter (optional)
- [ ] Announce Release in Newsletter (optional)
- [ ] Produce a release highlight video (optional)
- [ ] Announce Release on Hacker News (optional)?
- [ ] Post an announcement in the GitHub [Discussions Announcement forum](https://github.com/stackabletech/community/discussions/categories/announcements) and make it a pinned discussion while at the same time removing the old pinned thread
- [ ] Post an announcement in Discord
- [ ] Post an announcement on DOK Community (Ping Lars)
- [ ] Post an announcement via OSBA (Ping Lars)
```

```[tasklist]
### Post-release tasks
- [ ] Bump Rust version. This can be done [in this file](https://github.com/stackabletech/operator-templating/blob/main/repositories.yaml) by changing `rust_version` and also for the ubi base image [here](https://github.com/stackabletech/docker-images/blob/main/ubi8-rust-builder/Dockerfile#L25). Please be aware that this action will change it for all repositories at the same time (when merging the templating PRs).
- [ ] Run renovate manually
- [ ] Check/bump ubi8 base image
- [ ] Create issue for release-specific Openshift certification
- [ ] Define product versions to include in the next release
```
