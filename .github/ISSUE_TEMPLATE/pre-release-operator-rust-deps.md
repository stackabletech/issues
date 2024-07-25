---
name: Pre-Release Operator Rust Updates
about: This template can be used to track the progress of Rust updates across our operators leading up to the Stackable release
title: "chore(tracking): Update Rust dependencies of operators for Stackable release XX.(X)X"
labels: ['epic']
assignees: ''
---

<!--
    Make sure to update the link in '.github/ISSUE_TEMPLATE/release.md' when
    you change the front matter above.
-->

<!--
    DO NOT REMOVE THIS COMMENT. It is intended for people who might copy/paste from the previous release issue.
    This was created by an issue template: https://github.com/stackabletech/issues/issues/new/choose.
-->

## Pre-Release Operator Rust Updates

<!--
    Replace 'TRACKING_ISSUE' with the applicable release tracking issue number.
-->

Part of <https://github.com/stackabletech/issues/issues/TRACKING_ISSUE>

Replace the items in the task lists below with the applicable Pull Requests

> [!TIP]
> Create branches with predictable names so the links below work. Remember
> to replace `xx.(x)x` with the appropriate release version:
>
> ```sh
> git stash -m "unsaved work"
> git fetch origin
> git checkout -b chore/bump-rust-deps-pre-xx.(x)x origin/main
> ```
>
> Then use the links below to automatically create applicable PRs for each operator
> using the PR template.

<!--
    The following list was generated by:

    # go to the stackable-templating repository, then run:
    yq '.repositories[].name' config/repositories.yaml \
    | sort \
    | xargs -I {} echo "- [ ] https://github.com/stackabletech/{}/compare/main..chore/bump-rust-deps-pre-$(date +%y.%-m)?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-$(date +%y.%-m)"
-->

```[tasklist]
### Operator Rust Updates
- [ ] https://github.com/stackabletech/airflow-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/commons-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/druid-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/edc-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/hbase-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/hdfs-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/hello-world-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/hive-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/kafka-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/listener-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/nifi-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/opa-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/secret-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/spark-k8s-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/superset-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/trino-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
- [ ] https://github.com/stackabletech/zookeeper-operator/compare/main..chore/bump-rust-deps-pre-24.7?quick_pull=1&template=pre-release-rust-deps.md&title=chore%3A+Bump+Rust+dependencies+pre-24.7
```