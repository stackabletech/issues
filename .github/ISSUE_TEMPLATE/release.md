---
name: Release
about: This template can be used to track the release process at Stackable
title: Release XX.(X)X
labels: ''
assignees: ''

---

# Stackable Release XX.(X)X

## Release checklists

### General pre-requisites (before feature freeze)

- [ ] Bump operator-rs to latest version in all operators. This should be done early in the release cycle to leave sufficient time for testing etc.

### Other release-specific pre-requisites
- [ ] ...

### Feature freeze

This will not be so crucial with release branches, but is nonetheless sensible as it will make it easier to cherry-pick any release-related bugfixes from main into the release branch.

### End of the release cycle (Release day)

#### Technical tasks
- [ ] Create release branches for docker-images and operators (see stackable-utils for script to create branches)
- [ ] Create release tag(s) for docker-images and operators (see stackable-utils for scripts to create tags)
- [ ] Update changelogs in main branches (see stackable-utils for script to do this)
- [ ] Check integration tests (see table below)
- [ ] Check getting started scripts (see table below)
- [ ] Check new stackablectl Stacks and Demos (see table below)
  - [ ] Test with locally updated (to new release number) `releases.yaml`
  - [ ] Check stackablectl release upgrade with deployed products (does everything still spin up?) 
- [ ] Update `release.yaml` in https://github.com/stackabletech/release/blob/main/releases.yaml

#### Documentation tasks
- [ ] Check the Changelog and/or issue labels to compile Release Highlights
- [ ] Write an upgrade guide
  - [ ] Document how to use stackablectl to uninstall all and install new release
  - [ ] Document how to use helm to uninstall all and install new release
  - [ ] Every breaking change of all our operators
  - [ ] List dropped supported product versions (if there are some)
  - [ ] List dropped supported operators (if there are some)
  - [ ] List supported k8s versions
- [ ] Sync supported k8s versions in the READMEs with what is in the release notes (and apply templating)
- [ ] Update version of main documentation repo
- [ ] Set the release to "Released" in the Feature Tracker and create a new release

Marketing tasks can now reference published documentation.

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
- [ ] Inform Kubernetes Podcast about Release (optional)
- [ ] Post an announcement in the GitHub [Discussions Announcement forum](https://github.com/stackabletech/community/discussions/categories/announcements)

### Post-release tasks
- [ ] Bump Rust version. This can be done [in this file](https://github.com/stackabletech/operator-templating/blob/main/repositories.yaml) by changing `rust_version` and also for the ubi base iamge [here](https://github.com/stackabletech/docker-images/blob/main/ubi8-rust-builder/Dockerfile#L25). Please be aware that this action will change it for all repositories at the same time (when merging the templating PRs).
- [ ] Run renovate manually
- [ ] Check/bump ubi8 base image
- [ ] Create issue for release-specific Openshift certification
- [ ] Define product versions to include in the next release

### stackablectl

Actions:
* Test new stacks

| stackablectl stack | status |
| :--- | :--- |
| | |
(extend as necessary)

* Test new demos

| stackablectl demo | status |
| :--- | :--- |
| | |
(extend as necessary)

### Operators

| Operator  | Integration tests | Getting started scripts |
| :--- | :---: | :--- |
| Airflow   |         |                              |
| Commons   |         |                              |
| Druid     |         |                              |
| HBase     |         |                              |
| HDFS      |         |                              |
| Hive      |         |                              |
| Kafka     |         |                              |
| Listener  |         |                              |
| NiFi      |         |                              | 
| OPA       |         |                              |
| Secret    |         |                              |
| Spark     |         |                              |
| Superset  |         |                              |
| Trino     |         |                              |
| ZooKeeper |         |                              |

