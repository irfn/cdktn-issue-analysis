# cdk-terrain Manual Triage Plan

**Source:** hashicorp/terraform-cdk (archived)
**Target:** open-constructs/cdk-terrain
**Created:** 2026-01-18

---

## Overview

| Item | Count | Action |
|------|-------|--------|
| PRs to merge/cherry-pick | 4 priority + 4 other | Review and merge |
| Tier 1 issues (Critical) | 3 | Create immediately |
| Tier 2 issues (TF Version Gap) | 3 | Create - high priority |
| Tier 3 issues (Core) | 7 | Create - high priority |
| Tier 4 issues (Medium) | 8+ | Create - medium priority |
| Issues to skip/verify | ~60 | Review before creating |

---

## Phase 1: Merge Open PRs

### Priority PRs (Merge Immediately)

These PRs fix known priority issues. Review and cherry-pick/merge.

| | PR | Fixes Issue | Description | Action |
|---|---|-------------|-------------|--------|
| ☐ | [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920) | [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | HCL synth remote config bug | **Merge** - Fixes important-soon |
| ☐ | [#3928](https://github.com/hashicorp/terraform-cdk/pull/3928) | [#3532](https://github.com/hashicorp/terraform-cdk/issues/3532) | replaceTriggeredBy interpolation | **Merge** - Lifecycle bug |
| ☐ | [#3925](https://github.com/hashicorp/terraform-cdk/pull/3925) | [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) | Pipenv fix + Poetry/UV support | **Merge** - 15 comments |
| ☐ | [#3934](https://github.com/hashicorp/terraform-cdk/pull/3934) | [#3206](https://github.com/hashicorp/terraform-cdk/issues/3206) | Parallel deploy stack locking | **Merge** - 7 comments |

### Other PRs (Review)

| | PR | Description | Action |
|---|---|-------------|--------|
| ☐ | [#3946](https://github.com/hashicorp/terraform-cdk/pull/3946) | Security fix (validator CVE) | **Review** - Security |
| ☐ | [#3917](https://github.com/hashicorp/terraform-cdk/pull/3917) | StringMapMap class | **Review** - New feature |
| ☐ | [#3913](https://github.com/hashicorp/terraform-cdk/pull/3913) | Go 1.24 WASM fix | **Review** - Compatibility |
| ☐ | [#3876](https://github.com/hashicorp/terraform-cdk/pull/3876) | hclOutput config fix | **Review** - Bug fix |
| ☐ | [#3861](https://github.com/hashicorp/terraform-cdk/pull/3861) | DEP0044 deprecation fix | **Review** - Deprecation |

### PRs to Skip

| PR | Reason |
|----|--------|
| [#3948](https://github.com/hashicorp/terraform-cdk/pull/3948) | IBM copyright headers - Not relevant |
| [#3939](https://github.com/hashicorp/terraform-cdk/pull/3939) | GitHub Actions - Review if CI setup differs |
| [#3893](https://github.com/hashicorp/terraform-cdk/pull/3893) | Stale docs example |

---

## Phase 2: Create Tier 1 Issues (Critical)

Create these issues in cdk-terrain immediately. They block users.

### Issue 1: punycode Deprecation

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) |
| | **Title** | DeprecationWarning: The `punycode` module is deprecated |
| | **Type** | Bug |
| | **Priority** | Critical |
| | **Complexity** | Low |
| | **Labels** | `bug`, `priority/critical`, `good-first-issue` |

**Description for new issue:**
```markdown
## Problem
Running any `cdktf` command on Node.js 21+ shows:
```
(node:529691) [DEP0040] DeprecationWarning: The `punycode` module is deprecated.
```

## Impact
- Affects all users on Node.js 21+
- Will become an error in future Node.js versions

## Solution
Identify and update the dependency using deprecated `punycode` core module.

## Original issue
Migrated from hashicorp/terraform-cdk#3640
```

---

### Issue 2: Provider Generation Fails

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) |
| | **Title** | CLI: provider generation fails on versions newer than 0.20.1 |
| | **Type** | Bug |
| | **Priority** | Critical (Blocking) |
| | **Complexity** | Medium |
| | **Labels** | `bug`, `priority/critical`, `cli` |

**Description for new issue:**
```markdown
## Problem
`cdktf provider add` fails on versions > 0.20.1.

Works on 0.20.1:
```
[INFO] Adding local provider registry.terraform.io/grafana/grafana...
Generated typescript constructs in the output directory: src/gen
```

Fails on >0.20.1:
```
[INFO] Adding local provider regi...
<error>
```

## Impact
- **Blocking** - Users cannot add providers on newer versions
- Forces users to stay on older version

## Investigation needed
- Compare `cdktf provider add` code between 0.20.1 and later versions
- Check for changes in provider schema handling

## Original issue
Migrated from hashicorp/terraform-cdk#3803
```

---

### Issue 3: HCL Synth Remote Config (if PR not merged)

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) |
| | **Title** | CLI: HCL synth generates incorrect remote configuration |
| | **Type** | Bug |
| | **Priority** | Critical |
| | **Complexity** | Low |
| | **Labels** | `bug`, `priority/critical`, `has-pr` |
| | **Note** | Check if [PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920) was merged first |

---

## Phase 3: Create Tier 2 Issues (Terraform Version Gap)

**Strategic priority** - Close the 8-version gap (TF 1.7-1.14).

### Issue 4: `removed` Block Support (TF 1.7)

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) |
| | **Title** | Support Terraform `removed` block (TF 1.7) |
| | **Type** | Enhancement |
| | **Priority** | High |
| | **Complexity** | Medium |
| | **Labels** | `enhancement`, `priority/high`, `terraform-version-gap` |

**Description for new issue:**
```markdown
## Description
Terraform 1.7 introduced `removed` blocks to orphan resources without destroying them.
https://developer.hashicorp.com/terraform/language/resources/syntax#removing-resources

## Use case
- Easier refactoring of CDKTF code
- Moving resources between stacks without manual state manipulation

## Implementation
1. Add `TerraformRemoved` construct class
2. Generate `removed` blocks in HCL output
3. Support `destroy = false` lifecycle option

## Example
```typescript
new TerraformRemoved(this, 'old-bucket', {
  from: 'aws_s3_bucket.old_bucket',
  lifecycle: { destroy: false }
});
```

## Original issue
Migrated from hashicorp/terraform-cdk#3638
```

---

### Issue 5: Provider Functions Support (TF 1.8)

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) |
| | **Title** | Support Terraform provider functions (TF 1.8) |
| | **Type** | Enhancement |
| | **Priority** | High |
| | **Complexity** | High |
| | **Labels** | `enhancement`, `priority/high`, `terraform-version-gap`, `provider-generator` |

**Description for new issue:**
```markdown
## Description
Terraform 1.8 (April 2024) introduced provider functions.
https://www.hashicorp.com/blog/terraform-1-8-adds-provider-functions-for-aws-google-cloud-and-kubernetes

Example: `aws_arn_parse()` function is not available in generated code.

## Implementation required
1. **provider-schema** - Parse provider functions from schema
2. **provider-generator** - Generate function wrappers
3. **lib** - Runtime support for calling provider functions

## Example (desired)
```typescript
import { Fn } from '@cdktf/provider-aws';
const parsed = Fn.arnParse(myArn);
```

## Original issue
Migrated from hashicorp/terraform-cdk#3686
```

---

### Issue 6: Ephemeral Resources Support (TF 1.10)

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) |
| | **Title** | Support Terraform ephemeral resources (TF 1.10) |
| | **Type** | Enhancement |
| | **Priority** | High |
| | **Complexity** | High |
| | **Labels** | `enhancement`, `priority/high`, `terraform-version-gap` |

**Description for new issue:**
```markdown
## Description
Terraform 1.10 introduced ephemeral resources - resources that exist only during a run and don't persist in state.
https://developer.hashicorp.com/terraform/language/resources/ephemeral

## Use cases
- Temporary credentials
- Short-lived tokens
- Secrets that shouldn't be stored in state

## Implementation required
1. Schema parsing - Detect ephemeral resource types
2. Code generation - Generate `ephemeral` blocks
3. Type system - Handle ephemeral resource references

## Original issue
Migrated from hashicorp/terraform-cdk#3886
```

---

## Phase 4: Create Tier 3 Issues (Core Functionality)

### Issue 7: Multi-Stack Diff Broken

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) |
| | **Title** | Unable to perform cdktf diff with multiple stacks and inter-stack dependencies |
| | **Type** | Bug |
| | **Priority** | High |
| | **Complexity** | Large |
| | **Labels** | `bug`, `priority/high`, `multi-stack`, `cli` |

---

### Issue 8: Cross-Stack Reference with Modules

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662) |
| | **Title** | Cross Stack Reference Not Working with Modules |
| | **Type** | Bug |
| | **Priority** | High |
| | **Complexity** | Medium |
| | **Labels** | `bug`, `priority/high`, `multi-stack`, `modules` |

---

### Issue 9: Cross-Stack Dependencies in Wrapper Constructs

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976) |
| | **Title** | Cross stack dependencies fail within wrapper constructs |
| | **Type** | Bug |
| | **Priority** | High |
| | **Complexity** | Medium |
| | **Labels** | `bug`, `priority/high`, `multi-stack` |

---

### Issue 10: toHaveResource() Testing Bug

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) |
| | **Title** | Unit testing - toHaveResource() reports "found no resources" |
| | **Type** | Bug |
| | **Priority** | High |
| | **Complexity** | Small |
| | **Labels** | `bug`, `priority/high`, `testing` |

---

### Issue 11: fullSynth Cross-Stack Bug

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538) |
| | **Title** | Testing: fullSynth generates incorrect stack with cross-stack references |
| | **Type** | Bug |
| | **Priority** | High |
| | **Complexity** | Medium |
| | **Labels** | `bug`, `priority/high`, `testing`, `multi-stack` |

---

### Issue 12: Python Testing.synth_scope Broken

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) |
| | **Title** | [Python] Testing.synth_scope is broken |
| | **Type** | Bug |
| | **Priority** | High |
| | **Complexity** | Small |
| | **Labels** | `bug`, `priority/high`, `testing`, `language/python` |

---

### Issue 13: Programmatic API

| | Field | Value |
|---|-------|-------|
| ☐ | **Original** | [#237](https://github.com/hashicorp/terraform-cdk/issues/237) |
| | **Title** | API to interact with terraform CLI programmatically |
| | **Type** | Enhancement |
| | **Priority** | Medium |
| | **Complexity** | Large |
| | **Labels** | `enhancement`, `priority/medium`, `feature-request` |

---

## Phase 5: Create Tier 4 Issues (Medium Priority)

| | Original | Title | Type | Labels |
|---|----------|-------|------|--------|
| ☐ | [#376](https://github.com/hashicorp/terraform-cdk/issues/376) | terraform.workspace equivalent | Enhancement | `enhancement`, `priority/medium` |
| ☐ | [#294](https://github.com/hashicorp/terraform-cdk/issues/294) | State locking handling | Enhancement | `enhancement`, `priority/medium` |
| ☐ | [#2437](https://github.com/hashicorp/terraform-cdk/issues/2437) | Provider upgrade workflow bugs | Bug | `bug`, `priority/medium` |
| ☐ | [#682](https://github.com/hashicorp/terraform-cdk/issues/682) | Lifecycle hooks | Enhancement | `enhancement`, `priority/medium` |
| ☐ | [#1686](https://github.com/hashicorp/terraform-cdk/issues/1686) | Higher-level Constructs | Enhancement | `enhancement`, `priority/medium` |
| ☐ | [#3532](https://github.com/hashicorp/terraform-cdk/issues/3532) | replaceTriggeredBy bug | Bug | `bug`, `priority/medium` |
| ☐ | [#3641](https://github.com/hashicorp/terraform-cdk/issues/3641) | Linux prebuilt binary missing | Bug | `bug`, `priority/medium`, `platform` |
| ☐ | [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) | OpenTofu support | Enhancement | `enhancement`, `priority/low`, `future` |

---

## Phase 6: Verify Before Creating

These issues need verification before migration. Check if still reproducible.

### Stale Issues (29 total)

| | Original | Title | Last Updated | Action |
|---|----------|-------|--------------|--------|
| ☐ | [#435](https://github.com/hashicorp/terraform-cdk/issues/435) | Making cdktf dynamic | 2021-07-02 | Verify relevance |
| ☐ | [#492](https://github.com/hashicorp/terraform-cdk/issues/492) | Extract common Terraform JSON types | 2022-04-04 | Verify relevance |
| ☐ | [#909](https://github.com/hashicorp/terraform-cdk/issues/909) | Unable to run on M1 with asdf-vm | 2021-09-02 | Likely fixed |
| ☐ | ... | See [Issues-Likely-Not-Needed.md](./Issues-Likely-Not-Needed.md) | | |

### Needs Reproduction (21 total)

| | Original | Title | Action |
|---|----------|-------|--------|
| ☐ | [#3106](https://github.com/hashicorp/terraform-cdk/issues/3106) | TLS: RuntimeError | Attempt to reproduce |
| ☐ | [#3187](https://github.com/hashicorp/terraform-cdk/issues/3187) | Unable to resolve AWS local credentials | Attempt to reproduce |
| ☐ | [#3621](https://github.com/hashicorp/terraform-cdk/issues/3621) | synth --hcl fails to render false, 0, "" | Attempt to reproduce |
| ☐ | ... | See [Issues-Likely-Not-Needed.md](./Issues-Likely-Not-Needed.md) | |

---

## Phase 7: Skip These Issues

Do not migrate these issues.

| Category | Count | Examples |
|----------|-------|----------|
| **Notices** | 3 | [#2146](https://github.com/hashicorp/terraform-cdk/issues/2146), [#2160](https://github.com/hashicorp/terraform-cdk/issues/2160), [#3032](https://github.com/hashicorp/terraform-cdk/issues/3032) |
| **Telemetry** | 2 | [#841](https://github.com/hashicorp/terraform-cdk/issues/841), [#1639](https://github.com/hashicorp/terraform-cdk/issues/1639) |
| **Watch command** | 5 | [#869](https://github.com/hashicorp/terraform-cdk/issues/869), [#870](https://github.com/hashicorp/terraform-cdk/issues/870), [#871](https://github.com/hashicorp/terraform-cdk/issues/871), [#1003](https://github.com/hashicorp/terraform-cdk/issues/1003), [#1105](https://github.com/hashicorp/terraform-cdk/issues/1105) |

### Decide Later

| Category | Count | Decision needed |
|----------|-------|-----------------|
| **Terraform Cloud** | 7 | Will cdk-terrain support TFC? |

---

## Suggested Labels for cdk-terrain

```
# Priority
priority/critical
priority/high
priority/medium
priority/low

# Type
bug
enhancement
documentation
question

# Component
cli
core
provider-generator
testing
modules
convert

# Status
needs-triage
needs-reproduction
has-pr
help-wanted
good-first-issue

# Special
terraform-version-gap
multi-stack
language/python
language/go
language/csharp
language/java
platform
```

---

## Progress Tracking

### Summary

| Phase | Total | Done | Remaining |
|-------|-------|------|-----------|
| Phase 1: PRs | 9 | 0 | 9 |
| Phase 2: Tier 1 | 3 | 0 | 3 |
| Phase 3: Tier 2 | 3 | 0 | 3 |
| Phase 4: Tier 3 | 7 | 0 | 7 |
| Phase 5: Tier 4 | 8 | 0 | 8 |
| Phase 6: Verify | ~50 | 0 | ~50 |
| Phase 7: Skip | ~10 | - | - |
| **Total** | **~80** | **0** | **~80** |

---

## Quick Reference

### Commands

```bash
# Create issue in cdk-terrain
gh issue create --repo open-constructs/cdk-terrain \
  --title "Title" \
  --body "Description" \
  --label "bug,priority/high"

# View original issue
gh issue view 3640 --repo hashicorp/terraform-cdk

# Cherry-pick PR
gh pr view 3920 --repo hashicorp/terraform-cdk
git cherry-pick <commit-sha>
```

### Links

- **Source repo:** https://github.com/hashicorp/terraform-cdk
- **Target repo:** https://github.com/open-constructs/cdk-terrain
- **Analysis docs:** [README.md](./README.md)
