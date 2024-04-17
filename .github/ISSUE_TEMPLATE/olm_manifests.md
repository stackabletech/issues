---
name: OLM Manifest Guide
about: A task list for OLM manifest generation for certification
title: 'OLM Manifests for release xxx'
labels: ''
assignees: ''

---

This is a list of steps you can follow to generate, install and test Operator Lifecycle Management (OLM) manifests for the Stackable Data Platform.

The manigest generation is fully automated for all operators except two: the `secret` and the `listener` operator. These two required manual intervention.

OLM manifests can be generated at any time and for any version of the operators (including `0.0.0-dev`) but it's specially needed after a platform release, to certify the new operator versions.

To generate manifests for a released version of the SDP, ensure that you checkout the appropriate branch of the operator repository and the openshift operator repository.

## Pre-requisites

In addition to the usual development tools like `git` and `Python` you need to clone the following repositories, idealy in the same location (this guide assumes `$HOME/repo/stackable`):

* https://github.com/stackabletech/stackable-utils - contains utility scripts that you'll use below
* https://github.com/stackabletech/openshift-certified-operators - a fork used to submit SDP operators for certification
* Operator repositories that you intend to use like:
  * https://github.com/stackabletech/airflow-operator/
  * https://github.com/stackabletech/druid-operator/
  * https://github.com/stackabletech/commons-operator/
  * ... and so on

This issue assumes you are generating OLM manifests for a released SDP version with the intention of certifying it. This means:

- [ ] All operator repositories have the required release branch. These releases have been tested and are generally available.
- [ ] All container images have been published to quay.io


## Secret operator

- [ ] Create release branch (from `main`) in the openshift operator repository

      cd $HOME/repo/stackable/openshift-certified-operators
      git switch -c stackable-secret-24.3.0
      
- [ ] Generate manifests
      
    ./olm/build-manifests.sh -r 24.3.0 -c $HOME/repo/stackable/openshift-certified-operators -o $HOME/repo/stackable/secret-operator

Options:
* `-r 24.3.0` is the SDP release
* `-c $HOME/repo/stackable/openshift-certified-operators` the location of the openshift operator repository
* `-o $HOME/repo/stackable/secret-operator` the location of the secret op

## Listener operator

    build-manifests.sh

## All other operators

    ./olm/build-manifests.py --openshift-versions 'v4.11-v4.15' --release 24.3.0 --repo-operator ~/repo/stackable/commons-operator

    ./olm/build-bundles.sh -r 24.3.0 -o commons -c ~/repo/stackable/openshift-certified-operators -d

This is a simple checklist of things to bear in mind when creating a new issue.

- [ ] Generate the manifests
- [ ] Manually do a check of the CSV file, etc.
- [ ] Install the operator
- [ ] Test the operator
- [ ] ...
