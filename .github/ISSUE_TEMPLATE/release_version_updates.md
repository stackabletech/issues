---
name: Product version updates
about: Use this template once per SDP release to track the product updates we need to do
title: Update products
labels: ''
assignees: ''

---

This issue tracks the product versions and the changes we need to do to them in our SDP release XX.XX.

The single source of truth for this data is a [spreadsheet](https://docs.google.com/spreadsheets/d/1uR6nJR3nMxSI51dPFbVJTqA4R3p7UkGU5acrXJNOyNQ/edit#gid=866098130) we filled colaboratively in a planning meeting.

## Acceptance 

We want to bump old and new product versions with the latest ubi image releases. This means bumping the stackable version and rerunning the build actions. This includes our [Java base image](https://github.com/stackabletech/docker-images/tree/main/java-base) which should be done before updating any Java based products.

### Base images

#### UBI8 Rust Builder

[ubi8-rust-builder](https://github.com/stackabletech/docker-images/blob/main/ubi8-rust-builder/Dockerfile)

```[tasklist]
- [ ] Update UBI version
- [ ] Update Cargo CycloneDX and Cargo Auditable
- [ ] Update Rust Toolchain version
```

#### Java Base

Nothing currently needs to be updated here

#### Stackable Base

[stackable-base](https://github.com/stackabletech/docker-images/blob/main/stackable-base/Dockerfile)

```[tasklist]
- [ ] Update UBI version
```

### Product Images

- `New` versions need to be added to `conf.py` and added to the documentation page for the operator
- `Deprecated` need to be updated in the documentation
- `Removed` need to be updated in `conf.py` and removed from the documentation page


#### Airflow

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Druid

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### HBase, Phoenix, Omid

NOTE: Make sure to also consider Omid & Phoenix

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### HDFS

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Hive

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Kafka

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### NiFi

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### OpenPolicyAgent (OPA)

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Spark

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Superset

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Trino

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### ZooKeeper

```[tasklist]
- [ ] New:
- [ ] Deprecated: 
- [ ] Removed:
- [ ] Documentation is updated
- [ ] Operator is updated
```

### Misc

```[tasklist]
- [ ] Update the Stackable DB
```
