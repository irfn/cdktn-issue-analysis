# Top 10 Priority Issues - Detailed Analysis

*See also: [README.md](./README.md) | [Open-PRs-Analysis.md](./Open-PRs-Analysis.md) | [Maintainers-Priority-Issues.md](./Maintainers-Priority-Issues.md)*

---

## Summary

| Rank | Issue | Title | Priority | Complexity | Has PR |
|------|-------|-------|----------|------------|--------|
| 1 | [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | punycode deprecation | important-soon | Low | No |
| 2 | [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | HCL synth remote config | important-soon | Low | **Yes** ([#3920](https://github.com/hashicorp/terraform-cdk/pull/3920)) |
| 3 | [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) | Provider generation fails | Blocking | Medium | No |
| 4 | [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) | `removed` block (TF 1.7) | **Version gap** | Medium | No |
| 5 | [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) | Provider functions (TF 1.8) | **Version gap** | High | No |
| 6 | [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) | Ephemeral resources (TF 1.10) | **Version gap** | High | No |
| 7 | [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) | Multi-stack diff broken | important-longterm | Large | No |
| 8 | [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | toHaveResource() broken | important-longterm | Small | No |
| 9 | [#237](https://github.com/hashicorp/terraform-cdk/issues/237) | Programmatic API | important-longterm | Large | No |
| 10 | [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) | OpenTofu support | Future | Medium | No |

**Note:** Terraform version support (TF 1.7-1.14) is prioritized over OpenTofu. CDKTF is currently 8 versions behind.

---

## Issue #1: punycode Deprecation Warning

| Field | Value |
|-------|-------|
| **Issue** | [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) |
| **Title** | DeprecationWarning: The `punycode` module is deprecated |
| **Priority** | `important-soon` |
| **Type** | Bug |
| **Created** | 2024-06-04 |
| **Updated** | 2025-11-12 |
| **Comments** | 9 |
| **Author** | Rom888 |

### Problem

Running any `cdktf` command on Node.js 21+ shows:
```
(node:529691) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
```

### Impact

- **Affects all users** on Node.js 21+
- Causes confusion and noise in CLI output
- Will become an error in future Node.js versions

### Root Cause

CDKTF or one of its dependencies uses the deprecated `punycode` core module instead of the npm package.

### Suggested Fix

1. Identify which dependency uses `punycode`
2. Either update the dependency or replace with userland `punycode` npm package
3. May require updating `whatwg-url` or similar dependency

### Complexity

**Low** - Dependency update or replacement

### For cdk-terrain

**Priority: Critical** - Affects all users on modern Node.js versions.

---

## Issue #2: HCL Synth Remote Config Bug

| Field | Value |
|-------|-------|
| **Issue** | [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) |
| **Title** | CLI: HCL synth generates incorrect remote configuration with workspaces |
| **Priority** | `important-soon` |
| **Type** | Bug |
| **Created** | 2024-08-12 |
| **Updated** | 2025-08-10 |
| **Comments** | 3 |
| **Has PR** | **Yes** - [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920) |

### Problem

When using `cdktf synth --hcl`, the remote backend configuration generates incorrect HCL:

**Expected:**
```hcl
workspaces {
  name = "test-stack"
}
```

**Actual:**
```hcl
workspaces = {
  name = "test-stack"
}
```

The extra `=` causes `terraform init` to fail.

### Impact

- Users cannot use HCL synth with remote backends (JFrog Artifactory, etc.)
- Workaround: Manually remove the `=` after synthesis

### Root Cause

HCL generation doesn't handle block syntax vs. attribute syntax correctly for `workspaces`.

### Suggested Fix

[PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920) is ready - cherry-pick immediately.

### Complexity

**Low** - Fix already exists in PR

### For cdk-terrain

**Priority: Critical** - Merge [PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920) immediately.

---

## Issue #3: Provider Generation Fails >0.20.1

| Field | Value |
|-------|-------|
| **Issue** | [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) |
| **Title** | CLI: provider generation fails on versions newer than 0.20.1 |
| **Priority** | Blocking |
| **Type** | Bug |
| **Created** | 2025-01-17 |
| **Updated** | 2025-01-17 |
| **Comments** | 0 |
| **Author** | glacion |

### Problem

`cdktf provider add` fails on CDKTF versions > 0.20.1.

**Works (0.20.1):**
```
[INFO] Pre-built provider does not exist for the given constraints.
[INFO] Adding local provider registry.terraform.io/grafana/grafana...
Generated typescript constructs in the output directory: src/gen
```

**Fails (>0.20.1):**
```
[INFO] Pre-built provider does not exist for the given constraints.
[INFO] Adding local provider regi...
<error>
```

### Impact

- **Blocking** - Users cannot add providers on newer CDKTF versions
- Forces users to stay on older CDKTF version
- Affects all providers that don't have pre-built packages

### Root Cause

Unknown - likely a regression in provider schema handling or code generation between 0.20.1 and later versions.

### Investigation Needed

1. Compare `cdktf provider add` code between 0.20.1 and 0.20.2+
2. Check for changes in provider schema handling
3. Test with multiple providers to reproduce

### Complexity

**Medium** - Requires debugging regression

### For cdk-terrain

**Priority: Critical** - This is a blocking issue. Users cannot generate providers.

---

## Issue #4: `removed` Block (Terraform 1.7)

| Field | Value |
|-------|-------|
| **Issue** | [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) |
| **Title** | removed block: orphan resources managed by cdktf/terraform |
| **Priority** | **Version gap** |
| **Type** | Enhancement |
| **Created** | 2024-05-29 |
| **Updated** | 2024-05-29 |
| **Comments** | 0 |
| **Author** | fathom-parth |

### Description

Terraform 1.7 introduced [`removed` blocks](https://developer.hashicorp.com/terraform/language/resources/syntax#removing-resources) to orphan resources without destroying them.

Current workaround for moving resources between stacks is complex (documented [here](https://developer.hashicorp.com/terraform/cdktf/examples-and-guides/refactoring#moving-resources-from-one-stack-to-another)).

### Impact

- Difficult to refactor CDKTF code
- Moving resources between stacks is error-prone
- Users must manually manipulate state

### Implementation Requirements

1. Add `TerraformRemoved` construct class
2. Generate `removed` blocks in HCL output
3. Support `destroy = false` lifecycle option

### Example (desired)

```typescript
new TerraformRemoved(this, 'old-bucket', {
  from: 'aws_s3_bucket.old_bucket',
  lifecycle: {
    destroy: false
  }
});
```

Generates:
```hcl
removed {
  from = aws_s3_bucket.old_bucket
  lifecycle {
    destroy = false
  }
}
```

### Complexity

**Medium** - New construct type

### For cdk-terrain

**Priority: High** - First step in closing the Terraform version gap. Improves refactoring experience.

---

## Issue #5: Provider Functions (Terraform 1.8)

| Field | Value |
|-------|-------|
| **Issue** | [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) |
| **Title** | provider-generator: Add support for provider functions |
| **Priority** | Version gap |
| **Type** | Enhancement |
| **Created** | 2024-08-02 |
| **Updated** | 2025-03-27 |
| **Comments** | 2 |
| **Author** | so0k |

### Description

Terraform 1.8 (April 2024) introduced [provider functions](https://www.hashicorp.com/blog/terraform-1-8-adds-provider-functions-for-aws-google-cloud-and-kubernetes). CDKTF doesn't support these.

Example: `aws_arn_parse()` function is not available in generated TypeScript code.

### Impact

- Users cannot use provider functions like `arn_parse`, `arn_build`, etc.
- CDKTF is 8 versions behind Terraform
- Significant functionality gap

### Implementation Requirements

1. **provider-schema** - Parse provider functions from schema
   - Update `packages/@cdktf/provider-schema/src/provider-schema.ts`
   - Update `packages/@cdktf/commons/src/provider-schema.ts`

2. **provider-generator** - Generate function wrappers
   - Create TypeScript/Python/Go/etc. function definitions
   - Handle function signatures and return types

3. **lib** - Runtime support for calling provider functions
   - Bridge between CDK code and Terraform function calls

### Example Usage (desired)

```typescript
import { Fn } from '@cdktf/provider-aws';

const parsed = Fn.arnParse(myArn);
// parsed.account, parsed.region, etc.
```

### Complexity

**High** - Requires changes across multiple packages

### For cdk-terrain

**Priority: High** - Closing the Terraform version gap is important for adoption.

---

## Issue #6: Ephemeral Resources (Terraform 1.10)

| Field | Value |
|-------|-------|
| **Issue** | [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) |
| **Title** | Support Terraform ephemeral resources |
| **Priority** | Version gap |
| **Type** | Enhancement |
| **Created** | 2025-05-28 |
| **Updated** | 2025-11-27 |
| **Comments** | 1 |
| **Author** | evanstachowiak |

### Description

Terraform 1.10 introduced [ephemeral resources](https://developer.hashicorp.com/terraform/language/resources/ephemeral) - resources that exist only during a Terraform run and don't persist in state.

Use cases:
- Temporary credentials
- Short-lived tokens
- Secrets that shouldn't be stored in state

### Impact

- Modern Terraform users cannot use ephemeral resources via CDKTF
- Security-conscious users need this for secret handling

### Implementation Requirements

1. **Schema parsing** - Detect ephemeral resource types
2. **Code generation** - Generate `ephemeral` blocks instead of `resource` blocks
3. **Type system** - Handle ephemeral resource references correctly

### Example (desired)

```typescript
new EphemeralAwsSecretsmanagerSecretVersion(this, 'secret', {
  secretId: 'my-secret'
});
```

Generates:
```hcl
ephemeral "aws_secretsmanager_secret_version" "secret" {
  secret_id = "my-secret"
}
```

### Complexity

**High** - New resource type, requires schema and codegen changes

### For cdk-terrain

**Priority: High** - Important for security-conscious users.

---

## Issue #7: Multi-Stack Diff Broken

| Field | Value |
|-------|-------|
| **Issue** | [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) |
| **Title** | Unable to perform cdktf diff when using multiple stacks with inter-stack dependencies |
| **Priority** | `important-longterm` |
| **Type** | Bug |
| **Created** | 2022-10-02 |
| **Updated** | 2023-12-12 |
| **Comments** | 6 |
| **Labels** | `feature/multi-stack`, `size/large`, `upstream/terraform` |
| **Author** | natemellendorf |

### Problem

`cdktf plan '*-stack'` or `cdktf diff '*-stack'` fails when stacks have inter-stack dependencies (cross-stack references).

### Impact

- Cannot preview changes across multiple dependent stacks
- Must plan/diff each stack individually in correct order
- Major pain point for multi-stack architectures

### Root Cause

Cross-stack references create Terraform outputs/data sources that require the dependent stack to be deployed first. The diff command doesn't handle this dependency chain.

### Related Issues

- [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662) - Cross Stack Reference Not Working with Modules
- [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976) - Cross stack dependencies fail within wrapper constructs
- [#3206](https://github.com/hashicorp/terraform-cdk/issues/3206) - One stack failure locks other stacks (has [PR #3934](https://github.com/hashicorp/terraform-cdk/pull/3934))

### Suggested Fix

1. Detect dependency order between stacks
2. Run diff in dependency order
3. Use cached/mocked outputs for dependent stacks that haven't changed

### Complexity

**Large** - Requires significant CLI changes

### For cdk-terrain

**Priority: High** - Multi-stack is a common pattern; this is a major pain point.

---

## Issue #8: toHaveResource() Testing Bug

| Field | Value |
|-------|-------|
| **Issue** | [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) |
| **Title** | Unit testing - toHaveResource() - found no resources instead |
| **Priority** | `important-longterm` |
| **Type** | Bug |
| **Created** | 2022-06-07 |
| **Updated** | 2024-08-06 |
| **Comments** | 14 |
| **Labels** | `testing`, `size/small` |
| **Author** | sebolabs |

### Problem

`toHaveResource()` matcher reports "Found no resources" even when resources exist in the synthesized stack.

```typescript
expect(Testing.synthScope((scope) => {
  new PortalStack(scope, 'test');
})).toHaveResource(AzureadApplication);
// FAIL: Expected azuread_application to be present. Found no azuread_application resources instead
```

### Impact

- Testing framework is unusable for many users
- 14 comments indicate widespread issue
- Blocks adoption of testing best practices

### Root Cause

Likely issues with:
1. Resource name matching (provider prefix handling)
2. Scope synthesis not including all resources
3. Matcher not traversing nested constructs

### Related Issues

- [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) - Python Testing.synth_scope is broken
- [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538) - fullSynth generates incorrect stack with cross-stack refs

### Complexity

**Small** - According to labels, but high impact

### For cdk-terrain

**Priority: High** - Testing is critical for developer experience.

---

## Issue #9: Programmatic API

| Field | Value |
|-------|-------|
| **Issue** | [#237](https://github.com/hashicorp/terraform-cdk/issues/237) |
| **Title** | API to interact with terraform cli |
| **Priority** | `important-longterm` |
| **Type** | Enhancement |
| **Created** | 2020-07-23 |
| **Updated** | 2023-09-23 |
| **Comments** | 17 |
| **Labels** | `size/large`, `feature/programmatic-api` |
| **Author** | JayDoubleu |

### Description

Request for a programmatic API to interact with Terraform CLI from CDK code.

**Desired usage:**
```python
app = App()
MyStack(app, "automate-everything")
synth = app.synth()
plan = app.plan(synth)

if plan.changes is not None:
    if len(plan.changes.module.custom.fruits) > 4:
       app.apply(synth, target='module.custom.fruits')
```

### Impact

- Enables advanced automation scenarios
- Allows conditional deployments based on plan output
- 17 comments indicates strong community interest

### Use Cases

1. **Conditional deployments** - Apply only if certain conditions met
2. **Custom approval workflows** - Integrate with external systems
3. **Drift detection** - Programmatically check for drift
4. **CI/CD integration** - Fine-grained control in pipelines

### Implementation Requirements

1. **Plan parsing** - Parse `terraform plan` JSON output
2. **Plan types** - TypeScript/Python types for plan changes
3. **Apply API** - Programmatic apply with targeting
4. **State API** - Read state programmatically

### Complexity

**Large** - Significant new API surface

### For cdk-terrain

**Priority: Medium** - High community interest but large scope. Consider as future roadmap item.

---

## Issue #10: OpenTofu Support

| Field | Value |
|-------|-------|
| **Issue** | [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) |
| **Title** | opentofu support for terraform-cdk |
| **Priority** | Future |
| **Type** | Enhancement |
| **Created** | 2024-04-16 |
| **Updated** | 2024-11-12 |
| **Comments** | 1 |
| **Author** | yuriy-yarosh |

### Description

Request to support [OpenTofu](https://opentofu.org/) as a Terraform replacement due to Terraform's BSL license change.

### Impact

- OpenTofu is 100% compatible with Terraform 1.6.x
- Some organizations migrating to OpenTofu for licensing reasons

### Implementation Requirements

1. **Binary detection** - Support `tofu` binary alongside `terraform`
2. **Version detection** - Parse OpenTofu version output
3. **Configuration** - Allow users to specify which binary to use
4. **Testing** - Test against both Terraform and OpenTofu

### Suggested Approach

```typescript
// cdktf.json
{
  "terraformBinary": "tofu"  // or "terraform" (default)
}
```

Or environment variable:
```bash
export CDKTF_TERRAFORM_BINARY=tofu
```

### Complexity

**Medium** - Requires changes across CLI and documentation

### For cdk-terrain

**Priority: Future** - Focus on Terraform version support first. OpenTofu can be considered once the version gap is closed.

---

## Implementation Roadmap

### Phase 1: Critical (Immediate)

| Issue | Action | Complexity |
|-------|--------|------------|
| [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | Merge [PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920) | Done |
| [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | Update punycode dependency | Low |
| [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) | Debug and fix provider generation | Medium |

### Phase 2: Terraform Version Gap (Short-term)

| Issue | Action | Complexity |
|-------|--------|------------|
| [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) | Add `removed` block support (TF 1.7) | Medium |
| [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) | Provider functions support (TF 1.8) | High |
| [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) | Ephemeral resources support (TF 1.10) | High |

### Phase 3: Core Improvements (Medium-term)

| Issue | Action | Complexity |
|-------|--------|------------|
| [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) | Fix multi-stack diff | Large |
| [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | Fix testing matchers | Small |

### Phase 4: Future (Long-term)

| Issue | Action | Complexity |
|-------|--------|------------|
| [#237](https://github.com/hashicorp/terraform-cdk/issues/237) | Programmatic API | Large |
| [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) | OpenTofu support | Medium |

---

## Raw Data

Issue details fetched and stored in:
- `/tmp/issue-*.json` (temporary)
- `./issue-analysis/data/all-open-issues.json` (permanent)
