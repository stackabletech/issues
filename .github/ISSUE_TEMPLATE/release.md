---
name: Release
about: This template can be used to track the release process at Stackable
title: Release XXXX.XX
labels: ''
assignees: ''

---

# Stackable Release XXXX-XX

## Release checklists

### General pre-requisites (before feature freeze)

- [ ] Run renovate manually
- [ ] Check/bump ubi8 base image (it should be possible to do this by merging the latest Renovate PR mentioning ubi8)
- [ ] Check/bump java base image (it should be possible to do this by merging the latest Renovate PR mentioning ubi8)
- [ ] Check/bump the vector base image
- [ ] Check/bump the stackable base image
- [ ] Bump Rust version. This can be done [in this file](https://github.com/stackabletech/operator-templating/blob/main/repositories.yaml) by changing `rust_version` and also for the ubi base iamge [here](https://github.com/stackabletech/docker-images/blob/main/ubi8-rust-builder/Dockerfile#L25). Please be aware that this action will change it for all repositories at the same time (when merging the templating PRs).
- [ ] Define product versions to include in the next release
- [ ] Bump operator-rs to latest version in all operators. This should be done early in the release cycle to leave sufficient time for testing etc.
- [ ] Run getting-started scripts if they have not yet been incorporated into integration tests

### Other release-specific pre-requisites
- [ ] ...

### Feature freeze

This will not be so crucial with release branches, but is nonetheless sensible as it will make it easier to cherry-pick any release-related bugfixes from main into the release branch.

### End of the release cycle (Release day)

#### Technical tasks
- [ ] Create release branches for docker-images and operators (see stackable-utils for script to create branches)
- [ ] Create release tag(s) for docker-images and operators (see stackable-utils for scripts to create tags)
- [ ] Check integration tests
- [ ] Check getting started scripts (optional, as may be covered by integration tests)
- [ ] Check new stackablectl Stacks and Demos
  - [ ] test with locally updated (to new release number) `releases.yaml`
- [ ] update `release.yaml` in https://github.com/stackabletech/release/blob/main/releases.yaml

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
- [ ] Post an announcement in the GitHub [Discussions Announcement forum](https://github.com/stackabletech/community/discussions/categories/announcements)

#### stackablectl

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

#### Operators

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
