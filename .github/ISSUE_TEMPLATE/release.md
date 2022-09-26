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
- [ ] Bump Rust version. This can be done [in this file](https://github.com/stackabletech/operator-templating/blob/main/repositories.yaml) by changing `rust_version`. Please be aware that this action will change it for all repositories at the same time (when merging the templating PRs).
- [ ] Define product versions to include in the next release

### Before feature freeze

- [ ] Bump operator-rs to latest version in all operators

### Feature freeze

### End of the release cycle (Release day)

#### Technical tasks
- [ ] Bump every operator to the latest operator-rs at some point before the feature freeze (meaning: at least once in the release cycle, and leaving sufficient time for testing etc.)
- [ ] Release operators that are part of the release (if release is needed), see separate checklist below
  - [ ] Set stable operator versions in the `docs/templating_vars.yaml` file before releasing, and back to nightly afterwards
  - [ ] Release the actual operator
  - [ ] Bump the operators to the new -nightly version
- [ ] Integration tests passed
- [ ] Update stackablectl/release.yaml to add the new release
- [ ] Demos updated if required

#### Documentation tasks
- [ ] Create a Changelog including Release Highlights
- [ ] Write an upgrade guide
  - [ ] Document how to use stackablectl to uninstall all and install new release
  - [ ] Document how to use helm to uninstall all and install new release
  - [ ] Every breaking change of all our operators
  - [ ] List dropped supported product versions (if there are some)
  - [ ] List dropped supported operators (if there are some)
  - [ ] List supported k8s versions
- [ ] Bump documentation
  - [ ] Update version of main documentation repo (when it is versioned in the future)

#### Marketing tasks
- [ ] Update the homepage banner (as long as we have it) to point to the new release
- [ ] Write a blogpost announcing the new release (optional)
- [ ] Produce a release highlight video (optional)

#### stackablectl

Actions:
* Bump and test versions used in demos and stacks

| stackablectl element | Who | Status |
| :--- | :--- | :--- |
| stack: kafka-druid-superset-s3 |  |  |
| stack: trino-superset-s3 | |  |
| stack: airflow | |  |
| stack: hdfs-hbase | | |
| demo: trino-taxi-data | | |
| demo: kafka-druid-earthquake-data | ||
| demo: kafka-druid-water-level-data | | |
| demo: hbase-hdfs-load-cycling-data | | |

#### Operators

Actions:
* Release
* Test getting started guides
* read/test docs and examples (where relevant)

| Operator  | Version | Getting started (who/status) | Docs (who/status) | Release blockers | PR  |
| :-------- | :-----: | :--------------------------- | :---------------- | :--------------- | :-- |
| Airflow   |         |                              |                   |                  |     |
| Commons   |         |                              |                   |                  |     |
| Druid     |         |                              |                   |                  |     |
| HBase     |         |                              |                   |                  |     |
| HDFS      |         |                              |                   |                  |     |
| Hive      |         |                              |                   |                  |     |
| Kafka     |         |                              |                   |                  |     |
| NiFi      |         |                              |                   |                  |     |
| OPA       |         |                              |                   |                  |     |
| Secret    |         |                              |                   |                  |     |
| Spark     |         |                              |                   |                  |     |
| Superset  |         |                              |                   |                  |     |
| Trino     |         |                              |                   |                  |     |
| ZooKeeper |         |                              |                   |                  |     |
