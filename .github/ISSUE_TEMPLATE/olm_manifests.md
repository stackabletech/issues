---
name: OLM Manifest Guide
about: A task list for OLM manifest generation for certification
title: 'OLM Manifests for release xxx'
labels: ''
assignees: ''

---

## Pre-requisites

TODO: stackable-utils, openshift cert repo, etc.

## Secret operator

    build-manifests.sh

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
