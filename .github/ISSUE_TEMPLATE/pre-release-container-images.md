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

> [!TIP]
> The Rust upgrades should be done as and when needed by developers, rather than being tied to the product selection for a release.
> Also, ensure `make run-dev` works before bumping the Rust version across the operators. 

#### UBI8 Rust Builder

[ubi8-rust-builder](https://github.com/stackabletech/docker-images/blob/main/ubi8-rust-builder/Dockerfile)

- [ ] Update UBI version hash in the Dockerfile (`FROM`)
- [ ] Update `RUST_DEFAULT_TOOLCHAIN_VERSION`
- [ ] Update `CARGO_CYCLONEDX_CRATE_VERSION`
- [ ] Update `CARGO_AUDITABLE_CRATE_VERSION`
- [ ] Update `PROTOC_VERSION`

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR here_
- [ ] _Link to operator-rs PR_
- [ ] _Link to operator-templating PR_
```

#### UBI9 Rust Builder

[ubi9-rust-builder](https://github.com/stackabletech/docker-images/blob/main/ubi9-rust-builder/Dockerfile)

- [ ] Update UBI version hash in the Dockerfile (`FROM`)
- [ ] Update `RUST_DEFAULT_TOOLCHAIN_VERSION`
- [ ] Update `CARGO_CYCLONEDX_CRATE_VERSION`
- [ ] Update `CARGO_AUDITABLE_CRATE_VERSION`
- [ ] Update `PROTOC_VERSION`

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR here_
- [ ] _Link to operator-rs PR_
- [ ] _Link to operator-templating PR_
```

#### Java Base and Devel

> [!CAUTION]
> Any additions to the `java-base` or `java-devel` versions need to be there before updating Java based products.

```[tasklist]
### Related Pull Requests
- [ ] Does anything need doing here?
```

#### Stackable Base

[stackable-base](https://github.com/stackabletech/docker-images/blob/main/stackable-base/Dockerfile)

- [ ] Update UBI version hash in the Dockerfile (`FROM`)
- [ ] Update `RUST_DEFAULT_TOOLCHAIN_VERSION`
- [ ] Update `CARGO_CYCLONEDX_CRATE_VERSION`
- [ ] Update `CARGO_AUDITABLE_CRATE_VERSION`
- [ ] Update `PROTOC_VERSION`
- [ ] Update `CONFIG_UTILS_VERSION`

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR here_
- [ ] _Link to operator-rs PR_
- [ ] _Link to operator-templating PR_
```

### Product Images

- Make sure to _also_ check any other dependencies we might use in a Docker image! (e.g. git sync, prometheus exporter etc.)

#### Airflow

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### Druid

> [!IMPORTANT]
> Bump the JVM to the latest supported version.

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
- [ ] Update the [druid-opa-authorizer](https://github.com/stackabletech/druid-opa-authorizer/) with the new set of versions
```

#### HBase, Phoenix, Omid

> [!IMPORTANT]
> Bump the JVM to the latest supported version.
>
> Also consider Omid & Phoenix

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### HDFS

> [!IMPORTANT]
> Bump the JVM to the latest supported version.

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
- [ ] Update Authorizer (if needed)
- [ ] Update Group Mapper (if needed)
- [ ] Update Rack Awareness (if needed)
```

#### Hive

> [!IMPORTANT]
> Bump the JVM to the latest supported version.

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### Kafka

> [!IMPORTANT]
> Bump the JVM to the latest supported version

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### NiFi

> [!IMPORTANT]
> Bump the JVM to the latest supported version

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### OpenPolicyAgent (OPA)

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### Spark

> [!IMPORTANT]
> Bump the JVM to the latest supported version.

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### Superset

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### Trino

> [!IMPORTANT]
> Bump the JVM to the latest supported version.
>
> Also consider updating trino-cli in the same PR.

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

#### ZooKeeper

> [!IMPORTANT]
> Bump the JVM to the latest supported version.

```[tasklist]
### Related Pull Requests
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet
- [ ] Update the versions used in the operator
- [ ] Update the versions used in demos
```

### Misc

```[tasklist]
- [ ] Update the Stackable DB
```
