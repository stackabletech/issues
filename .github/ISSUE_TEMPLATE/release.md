---
name: Release
about: This template can be used to track the release process at Stackable
title: Release XXXX.XX
labels: ''
assignees: ''

---

# Stackable Release XXXX-XX

## Release checklists

### Beginning of the release cycle

- [ ] Bump ubi8 base image versions in https://github.com/stackabletech/docker-images (it should be possible to do this by merging the latest Renovate PR mentioning ubi8)
- [ ] Bump java base image versions in https://github.com/stackabletech/docker-images/tree/main/java-base (it should be possible to do this by merging the latest Renovate PR mentioning ubi8)
- [ ] Bump Rust version. This can be done [in this file](https://github.com/stackabletech/operator-templating/blob/main/repositories.yaml) by changing `rust_version`. Please be aware that this action will change it for all repositories at the same time (when merging the templating PRs).
- [ ] Define product versions to include in the next release

### Before feature freeze

- [ ] Bump operator-rs to latest version in all operators. When using release branches, this will usually be the previous platform release version. This should be done early in the release cycle to leave sufficient time for testing etc.

One-off tasks before the first release using release branches:

- [ ] Ensure that versions in the main branches for the the operators have been set to "0.0.0-nightly" (this will remain unchanged in the main branch)
- [ ] Ensure that automatic renovate runs have been disabled and do it manually once (or more if needed) at the beginning of the dev cycle (we update the dependencies *after the release is complete* in the *main* branch - never in release branches)

### Feature freeze

This will not be so crucial as we are using release branches, but is nonetheless sensible as it will make it easier to cherry-pick any release-related bugfixes from main into the release branch.

### End of the release cycle (Release day)

#### Technical tasks
- [ ] Create release branches for docker-images and operators (see stackable-utils for script to create branches)
- [ ] Create release tag(s) for docker-images and operators (see stackable-utils for scripts to create tags)
- [ ] Check integration tests
- [ ] Check all stackablectl Stacks and Demos

#### Documentation tasks
- [ ] Check the Changelog and/or issue labels to compile Release Highlights
- [ ] Write an upgrade guide
  - [ ] Document how to use stackablectl to uninstall all and install new release
  - [ ] Document how to use helm to uninstall all and install new release
  - [ ] Every breaking change of all our operators
  - [ ] List dropped supported product versions (if there are some)
  - [ ] List dropped supported operators (if there are some)
  - [ ] List supported k8s versions
  - [ ] Update version of main documentation repo
- [ ] Sync supported k8s versions in the READMEs with what is in the release notes (and apply templating)

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
* Test stacks

| stackablectl stack | Who | Status |
| :--- | :--- | :--- |
| stack: kafka-druid-superset-s3 |  |  |
| stack: trino-superset-s3 | |  |
| stack: airflow | |  |
| stack: hdfs-hbase | | |
(extend as necessary)

* Test demos

| stackablectl demo | Who | Status |
| :--- | :--- | :--- |
| demo: trino-taxi-data | | |
| demo: kafka-druid-earthquake-data | ||
| demo: kafka-druid-water-level-data | | |
| demo: hbase-hdfs-load-cycling-data | | |
(extend as necessary)

#### Operators

Actions:
* Release
* Test getting started guides
* read/test docs (and examples where relevant)

| Operator  | Version | Getting started (who/status) | Docs (who/status) | Release blockers | PR  |
| :--- | :---: | :--- | :--- | :--- | :--- |
| Commons   |         |                              |                   |                  |     |
| Secret    |         |                              |                   |                  |     |
| Listener  |         |                              |                   |                  |     |
| OPA       |         |                              |                   |                  |     |
| ZooKeeper |         |                              |                   |                  |     |
| Kafka     |         |                              |                   |                  |     |
| HDFS      |         |                              |                   |                  |     |
| Hive      |         |                              |                   |                  |     |
| HBase     |         |                              |                   |                  |     |
| NiFi      |         |                              |                   |                  |     |
| Druid     |         |                              |                   |                  |     |
| Trino     |         |                              |                   |                  |     |
| Spark     |         |                              |                   |                  |     |
| Airflow   |         |                              |                   |                  |     |
| Superset  |         |                              |                   |                  |     |
