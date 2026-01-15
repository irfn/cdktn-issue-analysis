# Open Pull Requests Analysis

*See also: [README.md](./README.md) | [Maintainers-Priority-Issues.md](./Maintainers-Priority-Issues.md) | [Most-Discussed-Issues.md](./Most-Discussed-Issues.md)*

---

## Summary

**12 open PRs** in hashicorp/terraform-cdk at time of archival.

| Category | Count | Action |
|----------|-------|--------|
| **Fixes Priority Issues** | 4 | Merge immediately / Review for cdk-terrain |
| **Bug Fixes** | 4 | Review and merge |
| **Maintenance/Deps** | 3 | Review for relevance |
| **Documentation** | 1 | Review |

### Key Finding

**4 PRs fix issues in our priority lists** - these should be reviewed immediately for cdk-terrain:

| PR | Fixes Issue | Issue Priority | PR Status |
|----|-------------|----------------|-----------|
| [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920) | [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | **important-soon** | Ready |
| [#3928](https://github.com/hashicorp/terraform-cdk/pull/3928) | [#3196](https://github.com/hashicorp/terraform-cdk/issues/3196) (related to [#3532](https://github.com/hashicorp/terraform-cdk/issues/3532)) | important-longterm | Ready |
| [#3925](https://github.com/hashicorp/terraform-cdk/pull/3925) | [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) | backlog (15 comments) | Ready |
| [#3934](https://github.com/hashicorp/terraform-cdk/pull/3934) | [#3206](https://github.com/hashicorp/terraform-cdk/issues/3206) | - (7 comments) | Ready |

---

## Tier 1: PRs Fixing Priority Issues

### [PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920) - HCL Remote Backend Fix

| Field | Value |
|-------|-------|
| **Title** | fix(lib): generate correct HCL for remote backend |
| **Fixes** | [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) (**important-soon**) |
| **Author** | Hi-Fi |
| **Created** | 2025-08-10 |
| **Changes** | +151/-9 in 2 files |
| **Status** | REVIEW_REQUIRED |

**Description:** Fixes incorrect `=` in workspace configuration when using remote backend (e.g., JFrog Artifactory).

**Priority:** **Critical** - This PR fixes a Tier 1 issue in our migration plan.

---

### [PR #3928](https://github.com/hashicorp/terraform-cdk/pull/3928) - replaceTriggeredBy Fix

| Field | Value |
|-------|-------|
| **Title** | fix(lib): properly interpolate dependencies in replaceTriggeredBy |
| **Fixes** | [#3196](https://github.com/hashicorp/terraform-cdk/issues/3196) |
| **Related** | [#3532](https://github.com/hashicorp/terraform-cdk/issues/3532) (important-longterm), [#3546](https://github.com/hashicorp/terraform-cdk/issues/3546) |
| **Author** | luke-chisholm6 |
| **Created** | 2025-09-15 |
| **Changes** | +34/-10 in 3 files |
| **Status** | REVIEW_REQUIRED |

**Description:** Fixes tokenized address generation in `replaceTriggeredBy` lifecycle attribute.

**Priority:** **High** - Addresses a known lifecycle bug affecting multiple languages.

---

### [PR #3925](https://github.com/hashicorp/terraform-cdk/pull/3925) - Python Package Manager Fix

| Field | Value |
|-------|-------|
| **Title** | fix(lib): Fixed bug where pipenv was always created, added support for poetry and uv |
| **Fixes** | [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) (15 comments) |
| **Author** | bendog |
| **Created** | 2025-08-25 |
| **Changes** | +308/-115 in 1 file |
| **Status** | REVIEW_REQUIRED |

**Description:**
- Fixes false positive pipenv detection when pipenv is installed but not used
- Adds support for Poetry and UV package managers (more popular than pipenv)

**Priority:** **High** - Fixes most-discussed Python issue (15 comments). Improves Python developer experience significantly.

---

### [PR #3934](https://github.com/hashicorp/terraform-cdk/pull/3934) - Parallel Deploy Fix

| Field | Value |
|-------|-------|
| **Title** | fix(cli-core): wait for running stacks to complete when one fails |
| **Fixes** | [#3206](https://github.com/hashicorp/terraform-cdk/issues/3206) (7 comments) |
| **Author** | aong-atlassian |
| **Created** | 2025-10-06 |
| **Changes** | +67/-1 in 3 files |
| **Status** | REVIEW_REQUIRED |

**Description:** Fixes critical bug where parallel stack deployments crash and leave infrastructure inconsistent when one stack fails. Previously, `Promise.race()` would throw immediately, causing running Terraform processes to be orphaned.

**Priority:** **High** - Fixes a significant multi-stack workflow issue.

---

## Tier 2: Other Bug Fixes

### [PR #3917](https://github.com/hashicorp/terraform-cdk/pull/3917) - StringMapMap Support

| Field | Value |
|-------|-------|
| **Title** | feat(lib): add StringMapMap class |
| **Fixes** | [#3915](https://github.com/hashicorp/terraform-cdk/issues/3915) |
| **Author** | nikolaymatrosov |
| **Created** | 2025-07-27 |
| **Changes** | +174/-1 in 6 files |

**Description:** Adds support for `map[map[string]]` type in provider schemas (needed by yandex-cloud provider).

---

### [PR #3913](https://github.com/hashicorp/terraform-cdk/pull/3913) - Go 1.24 WASM Fix

| Field | Value |
|-------|-------|
| **Title** | fix(hcl2cdk): Improve wasm_exec.js file detection in prebuild script |
| **Fixes** | [#3912](https://github.com/hashicorp/terraform-cdk/issues/3912) |
| **Author** | nikolaymatrosov |
| **Created** | 2025-07-13 |
| **Changes** | +16/-8 in 2 files |

**Description:** Fixes compatibility with Go 1.24 WebAssembly changes.

---

### [PR #3876](https://github.com/hashicorp/terraform-cdk/pull/3876) - hclOutput Config Fix

| Field | Value |
|-------|-------|
| **Title** | fix(lib): respect hclOutput app config |
| **Fixes** | [#3875](https://github.com/hashicorp/terraform-cdk/issues/3875) |
| **Author** | jyecusch |
| **Created** | 2025-05-22 |
| **Changes** | +2/-5 in 3 files |
| **Comments** | 6 |

**Description:** Properly respects `hclOutput` configuration from App class and `SYNTH_HCL_OUTPUT` env var.

---

### [PR #3861](https://github.com/hashicorp/terraform-cdk/pull/3861) - Deprecation Fix

| Field | Value |
|-------|-------|
| **Title** | fix(lib): DEP0044 in TerraformOutput |
| **Fixes** | [#3860](https://github.com/hashicorp/terraform-cdk/issues/3860) |
| **Author** | gabegorelick |
| **Created** | 2025-04-23 |
| **Changes** | +1/-2 in 1 file |
| **Comments** | 10 |

**Description:** Replaces deprecated `util.isArray` with `Array.isArray`.

---

## Tier 3: Maintenance & Dependencies

### [PR #3948](https://github.com/hashicorp/terraform-cdk/pull/3948) - Copyright Headers

| Field | Value |
|-------|-------|
| **Title** | [COMPLIANCE] Update Copyright Headers |
| **Author** | oss-core-libraries-dashboard (bot) |
| **Labels** | legal, automated |
| **Changes** | +895/-895 in 893 files |

**Description:** IBM compliance update for copyright headers.

**For cdk-terrain:** Not relevant - will need own copyright/license headers.

---

### [PR #3946](https://github.com/hashicorp/terraform-cdk/pull/3946) - Security Update

| Field | Value |
|-------|-------|
| **Title** | chore(deps): Update dependency validator to v13.15.23 |
| **Author** | robinvw1 |
| **Fixes** | [GHSA-9965-vmph-33xx](https://github.com/advisories/GHSA-9965-vmph-33xx) |
| **Labels** | - |
| **Changes** | +5/-5 in 2 files |

**Description:** Security fix for validator package CVE.

**For cdk-terrain:** **Review** - Security fixes should be applied.

---

### [PR #3939](https://github.com/hashicorp/terraform-cdk/pull/3939) - GitHub Actions Update

| Field | Value |
|-------|-------|
| **Title** | chore(deps): bump github-actions-breaking group |
| **Author** | dependabot |
| **Labels** | dependencies, security |
| **Changes** | +63/-63 in 15 files |

**Description:** Updates GitHub Actions (checkout v5, upload-artifact v5, download-artifact v6, setup-terraform v3).

**For cdk-terrain:** **Review** - CI updates may be relevant.

---

## Tier 4: Documentation

### [PR #3893](https://github.com/hashicorp/terraform-cdk/pull/3893) - Conditional Example

| Field | Value |
|-------|-------|
| **Title** | chore(examples): Document conditional |
| **Fixes** | [#2915](https://github.com/hashicorp/terraform-cdk/issues/2915) |
| **Author** | covracer |
| **Labels** | stale |
| **Changes** | +115/-20 in 4 files |

**Description:** Adds example for `Fn.conditional()` usage.

---

## PR Age Analysis

| Age | PRs | Notes |
|-----|-----|-------|
| < 1 month | 2 | [#3948](https://github.com/hashicorp/terraform-cdk/pull/3948), [#3946](https://github.com/hashicorp/terraform-cdk/pull/3946) |
| 1-3 months | 3 | [#3939](https://github.com/hashicorp/terraform-cdk/pull/3939), [#3934](https://github.com/hashicorp/terraform-cdk/pull/3934), [#3928](https://github.com/hashicorp/terraform-cdk/pull/3928) |
| 3-6 months | 4 | [#3925](https://github.com/hashicorp/terraform-cdk/pull/3925), [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920), [#3917](https://github.com/hashicorp/terraform-cdk/pull/3917), [#3913](https://github.com/hashicorp/terraform-cdk/pull/3913) |
| > 6 months | 3 | [#3893](https://github.com/hashicorp/terraform-cdk/pull/3893), [#3876](https://github.com/hashicorp/terraform-cdk/pull/3876), [#3861](https://github.com/hashicorp/terraform-cdk/pull/3861) |

---

## Recommendations for cdk-terrain

### Immediate Actions

1. **Cherry-pick [PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920)** - Fixes important-soon issue [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698)
2. **Review [PR #3928](https://github.com/hashicorp/terraform-cdk/pull/3928)** - Fixes replaceTriggeredBy bug ([#3532](https://github.com/hashicorp/terraform-cdk/issues/3532))
3. **Review [PR #3925](https://github.com/hashicorp/terraform-cdk/pull/3925)** - Fixes pipenv issue + adds Poetry/UV support
4. **Review [PR #3934](https://github.com/hashicorp/terraform-cdk/pull/3934)** - Fixes parallel deploy issue

### Review for Inclusion

5. **[PR #3946](https://github.com/hashicorp/terraform-cdk/pull/3946)** - Security fix (validator CVE)
6. **[PR #3917](https://github.com/hashicorp/terraform-cdk/pull/3917)** - StringMapMap feature
7. **[PR #3913](https://github.com/hashicorp/terraform-cdk/pull/3913)** - Go 1.24 compatibility

### Skip

- **[PR #3948](https://github.com/hashicorp/terraform-cdk/pull/3948)** - IBM copyright headers (not relevant)
- **[PR #3893](https://github.com/hashicorp/terraform-cdk/pull/3893)** - Stale, docs only

---

## Language-Specific PRs

| Language | PRs |
|----------|-----|
| Python | [PR #3925](https://github.com/hashicorp/terraform-cdk/pull/3925) (pipenv/poetry/uv) |
| Go | [PR #3913](https://github.com/hashicorp/terraform-cdk/pull/3913) (Go 1.24 WASM) |
| Core (all languages) | [PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920), [PR #3928](https://github.com/hashicorp/terraform-cdk/pull/3928), [PR #3934](https://github.com/hashicorp/terraform-cdk/pull/3934), [PR #3917](https://github.com/hashicorp/terraform-cdk/pull/3917), [PR #3876](https://github.com/hashicorp/terraform-cdk/pull/3876), [PR #3861](https://github.com/hashicorp/terraform-cdk/pull/3861) |

---

## Raw Data

```
./issue-analysis/data/all-open-prs.json    # All 12 open PRs
```
