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

We want to bump old and new product versions with the latest ubi image releases.
This includes our [Java base image](https://github.com/stackabletech/docker-images/tree/main/java-base) which should be done before updating any Java based products.
It also includes bumping to the latest supported JVM version.

### Base images

#### UBI8 Rust Builder

[ubi8-rust-builder](https://github.com/stackabletech/docker-images/blob/main/ubi8-rust-builder/Dockerfile)

```[tasklist]
- [ ] Update UBI version
- [ ] Update Cargo CycloneDX and Cargo Auditable
- [ ] Update Rust Toolchain version
- [ ] Update `protoc` version
```

#### UBI9 Rust Builder

[ubi9-rust-builder](https://github.com/stackabletech/docker-images/blob/main/ubi9-rust-builder/Dockerfile)

```[tasklist]
- [ ] Update UBI version
- [ ] Update Cargo CycloneDX and Cargo Auditable
- [ ] Update Rust Toolchain version
- [ ] Update `protoc` version
```

#### Java Base

Nothing currently needs to be updated here

#### Stackable Base

[stackable-base](https://github.com/stackabletech/docker-images/blob/main/stackable-base/Dockerfile)

```[tasklist]
- [ ] Update UBI version
- [ ] Update Cargo CycloneDX and Cargo Auditable
- [ ] Update Rust Toolchain version
- [ ] Update `protoc` version
- [ ] Update config-utils version
```

### Product Images

- Make sure to _also_ check any other dependencies we might use in a Docker image! (e.g. git sync, prometheus exporter etc.)

#### Airflow

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Druid

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
- [ ] Update the [druid-opa-authorizer](https://github.com/stackabletech/druid-opa-authorizer/) with the new set of versions
```

#### HBase, Phoenix, Omid

NOTE: Make sure to also consider Omid & Phoenix

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### HDFS

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
- [ ] Update Authorizer, Group Mapper and Rack Awareness stuff if needed
```

#### Hive

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Kafka

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### NiFi

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### OpenPolicyAgent (OPA)

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Spark

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Superset

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### Trino

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] Documentation is updated
- [ ] Operator is updated
```

#### ZooKeeper

```[tasklist]
- [ ] Versions are updated in accordinance to the source of truth spreadsheet
- [ ] JVM is at latest supported version
- [ ] Documentation is updated
- [ ] Operator is updated
```

### Misc

```[tasklist]
- [ ] Update the Stackable DB
```
