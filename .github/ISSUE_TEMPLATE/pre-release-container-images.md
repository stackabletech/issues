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

These high level tasks need to be completed.

> [!IMPORTANT]
> At the end, these should be checked based on the more granular criterea for each product/image below.

- [ ] Bump UBI Image releases.
- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update product version references in getting_started docs, kuttl tests, and demos.
- [ ] Update the Stackable DB.

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

#### Vector

> [!CAUTION]
> Any additions to the versions need to be there before updating the `java-base`.

Used as a base for `java-base`.

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
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

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### Druid

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Update the [druid-opa-authorizer](https://github.com/stackabletech/druid-opa-authorizer/) with the new set of versions.
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
- [ ] _Link to [druid-opa-authorizer](https://github.com/stackabletech/druid-opa-authorizer/) PR_
```

#### HBase, Phoenix, Omid

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.
- [ ] Update Omid.
- [ ] Update Phoenix.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### HDFS

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.
- [ ] Check Authorizer (unknown procedure)
- [ ] Check Group Mapper (unknown procedure)
- [ ] Check Rack Awareness (unknown procedure)

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### Hive

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### Kafka

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### NiFi

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### OpenPolicyAgent (OPA)

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### Spark

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### Superset

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### Trino

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.
- [ ] Update trino-cli.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```

#### ZooKeeper

**Acceptance criterea:**

- [ ] Update `versions.py` to reflect the agreed upon versions in the spreadsheet.
- [ ] Update `versions.py` to the latest supported version of JVM (base and devel).
- [ ] Check other operators (getting_started / kuttl) for usage of the versions. Add the PR to the list below.

```[tasklist]
### Related Pull Requests
- [ ] _Link to PR_
- [ ] _Link to operator PR (getting_started / kuttl)_
- [ ] _Link to other operator PRs (getting_started / kuttl)_
- [ ] _Link to demo PR (Do not merge until demos are released)_
```
