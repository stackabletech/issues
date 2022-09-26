---
name: Product version updates
about: This template can be used to track the versions of the products we want to release
title: Update products
labels: ''
assignees: ''

---

This ticket is used to fix the versions of upstream products we want to support (in addition to the currently supported ones).
We do _not_ need to always support the latest versions.
For example: With new major and minor releases we _may_ want to wait for a first patch release (e.g. don't support 3.0.0 but 3.0.1 instead, or 2.4.2 instead of 2.4.0).

In addition to the new and/or removed product versions we also want to update our base image to a new version at least once per release.

# Product versions

_Legend_:
* _Latest (Upstream)_: The latest upstream version of the product
* _Latest (Stackable)_: The latest version that we at Stackable currently support
* _New_: A list of new versions we want to support in the upcoming release
* _Removed_: A list of versions we will not support anymore

| Product   | Latest (Upstream) | Latest (Stackable) | New | Removed |
|-----------|-------------------|--------------------|-----|---------|
| Airflow   | | | | |
| Druid     | | | | |
| HBase     | | | | |
| HDFS      | | | | |
| Hive      | | | | |
| Kafka     | | | | |
| NiFi      | | | | |
| OPA       | | | | |
| Spark-k8s | | | | |
| Superset  | | | | |
| Trino     | | | | |
| ZooKeeper | | | | |

## Acceptance 

We want to bump old and new product versions with the latest ubi image releases. This means bumping the stackable version and rerunning the build actions. This includes our [Java base image](https://github.com/stackabletech/docker-images/tree/main/java-base) which shouldbe done before updating any Java based products.

### Base images

- [ ] Java base image
- [ ] Airflow
- [ ] Druid
- [ ] HBase
- [ ] Hadoop HDFS
- [ ] Hive
- [ ] Kafka
- [ ] NiFi
- [ ] OPA
- [ ] Spark
- [ ] Superset
- [ ] Trino
- [ ] ZooKeeper

### New versions

This is a tasklist pointing to issues in the product repositories:

- [ ] ....
