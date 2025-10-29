---
name: OLM Manifest Guide
about: A task list for OLM manifest generation for certification
title: 'chore(tracking): OLM Manifests for SDP Release YY.M.X'
labels: ''
assignees: ''
---

This is for tracking distributed work. For instructions on how to proceed with each operator, see the description below.

Please follow this list in order at least until the zookeeper-operator before parallelizing.

| Operator   | Maintainer | Branch                  | Kuttl Tests        | Cert Pipeline PR    | Notes |
| ---------- | ---------- | ----------------------- | ------------------ | ------------------- | ----- |
| commons    | GH handle  | branch name in the fork | :white_check_mark: | link to upstream PR |       |
| secret     |            |                         |                    |                     |       |
| listener   |            |                         |                    |                     |       |
| zookeeper  |            |                         |                    |                     |       |
| hdfs       |            |                         |                    |                     |       |
| hive       |            |                         |                    |                     |       |
| hbase      |            |                         |                    |                     |       |
| opa        |            |                         |                    |                     |       |
| opensearch |            |                         |                    |                     |       |
| druid      |            |                         |                    |                     |       |
| kafka      |            |                         |                    |                     |       |
| nifi       |            |                         |                    |                     |       |
| spark      |            |                         |                    |                     |       |
| superset   |            |                         |                    |                     |       |
| airflow    |            |                         |                    |                     |       |
| trino      |            |                         |                    |                     |       |

## Description

This is a list of steps you can follow to generate, install and test Operator Lifecycle Management (OLM) manifests for the Stackable Data Platform.

The manigest generation is fully automated for all operators except two: the `secret` and the `listener` operator. These two required manual intervention.

OLM manifests can be generated at any time and for any version of the operators (including `0.0.0-dev`) but it's specially needed after a platform release, to certify the new operator versions.

To generate manifests for a released version of the SDP, ensure that you checkout the appropriate branch of the operator repository and the openshift operator repository.

### Pre-requisites

In addition to the usual development tools like `git` and `Python` you need to clone the following repositories, idealy in the same location (this guide assumes `$HOME/repo/stackable`):

- <https://github.com/stackabletech/stackable-utils> - contains utility scripts that you'll use below
- <https://github.com/stackabletech/openshift-certified-operators> - a fork used to submit SDP operators for certification
- Operator repositories that you intend to use like:
  - <https://github.com/stackabletech/airflow-operator/>
  - <https://github.com/stackabletech/druid-operator/>
  - <https://github.com/stackabletech/commons-operator/>
  - ... and so on

This issue assumes you are generating OLM manifests for a released SDP version with the intention of certifying it. This means:

- [ ] All operator repositories have the required release branch. These releases have been tested and are generally available.
- [ ] All container images have been published to quay.io

### Secret and listener operator

#### Generate manifests

- [ ] Update the supported OpenShift version range in the function [generate_metadata()](https://github.com/stackabletech/stackable-utils/blob/273ec983d6c0b1ea1852d9633ed56b8123054b39/olm/build-manifests.sh#L39)
- [ ] Create release branch (from `main`) in the openshift operator repository

  ```shell
  cd $HOME/repo/stackable/openshift-certified-operators
  git switch -c stackable-secret-YY.M.X
  ```

- [ ] Generate manifests

  ```shell
  ./olm/build-manifests.sh -r YY.M.X \
  -c $HOME/repo/stackable/openshift-certified-operators \
  -o $HOME/repo/stackable/secret-operator
  ```

Options:

- `-r YY.M.X` is the SDP release
- `-c $HOME/repo/stackable/openshift-certified-operators` the location of the openshift operator repository
- `-o $HOME/repo/stackable/secret-operator` the location of the secret op

- [ ] Copy the cluster service version file from the previous  version.
- [ ] Copy the operator manifests file from the previous version. For [secret](https://github.com/stackabletech/openshift-certified-operators/blob/main/operators/stackable-secret-operator/OO.M.X/manifests/secret-operator-manifests.yaml) and [listener](https://github.com/stackabletech/openshift-certified-operators/blob/main/operators/stackable-listener-operator/OO.M.X/manifests/listener-operator-manifests.yaml)
- [ ] Replace the contents of the deployment, and cluster role with the `template.spec` and `rules` from the newly generated files.
- [ ] Remove the unused generated files : service account, operator cluster role (not the product cluster role), role binding, deployment.
- [ ] Remove all Helm labels in all remaining files (including all labels from the cluster role).
- [ ] Check or update the metadata/dependencies.yaml
- [ ] Update image tags and hashes with quay.io versions
- [ ] Commit & push your changes

#### Install manifests

- [ ] Ensure your K8S configuration points to a an OpenShift (or OKD) instance
- [ ] Install the operator from the manifests generated in the previous step

  ```shell
  /olm/build-bundles.sh -r YY.M.X -o secret -c ~/repo/stackable/openshift-certified-operators -d
  ```

Options:

- `-r YY.M.X` version of the operator to install
- `-o secret` name of the operator to install
- `-c ~/repo/stackable/openshift-certified-operators` location of the openshift operator repository
- `-d` deploy to the cluster

### All other operators

These operators shouldn't require any manual editing of the manifests but a visual check is recommended.

The steps are illustrated only once for the ZooKeeper operator but a list of all operators to work on is added below.

#### Generate manifests

- [ ] Create release branch (from `main`) in the openshift operator repository

  ```shell
  cd $HOME/repo/stackable/openshift-certified-operators
  git switch -c stackable-zookeeper-YY.M.X
  ```

- [ ] Ensure appropriate branch (`release-YY.M`) is checkout out in the ZooKeeper operator
- [ ] Generate manifests

  ```shell
  ./olm/build-manifests.py  \
  --openshift-versions v4.14-v4.16 \
  --repo-certified-operators ~/repo/stackable/openshift-certified-operators \
  --channel YY.M \
  --release YY.M.X \
  --replaces OO.M.X \
  --repo-operator ~/repo/stackable/zookeeper-operator
  ```

See `./olm/build-manifests.py --help` for possible options.

#### Install manifests

```shell
./olm/build-bundles.sh \
-r YY.M.X \
-o zookeeper \
-c ~/repo/stackable/openshift-certified-operators \
-d
```

#### Test the operator

Run the openshit integration test suite for the operator

```shell
cd ~/repo/stackable/zookeeper-operator
/scripts/run-tests --test-suite openshift --skip-operator zookeeper
```

We use `--skip-operator` because the operator has already been installed previously.
