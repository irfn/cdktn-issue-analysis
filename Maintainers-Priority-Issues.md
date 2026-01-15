# terraform-cdk Maintainers Priority Issues

**Source:** https://github.com/hashicorp/terraform-cdk (archived)
**Target:** https://github.com/open-constructs/cdk-terrain
**Analysis Date:** 2026-01-15

## Overview

- **Total Open Issues:** 380
- **Prioritized by Maintainers:** 215 issues
  - `priority/important-soon`: 4 issues (highest priority)
  - `priority/important-longterm`: 113 issues
  - `priority/backlog`: 98 issues

*Documentation issues (65) tracked separately in [Documentation-Issues.md](./Documentation-Issues.md)*

## Priority Tiers

### Tier 1: `priority/important-soon` (2 non-docs issues) - MIGRATE IMMEDIATELY

| # | Title | Type |
|---|-------|------|
| [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | DeprecationWarning: The `punycode` module is deprecated | bug |
| [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | CLI: HCL synth generates incorrect remote configuration with workspaces | bug |

### Tier 2: `priority/important-longterm` by Component (excluding docs)

| Component | Count | Notes |
|-----------|-------|-------|
| CLI (cdktf-cli) | 21 | Core CLI functionality |
| Core Library (cdktf) | 20 | Core library issues |
| Providers/Generation | 11 | Provider generation issues |
| Convert (HCL) | 9 | HCL-to-CDKTF conversion |
| Testing | 8 | Testing framework issues |
| Modules | 5 | Module-related issues |

### Key Bugs in `priority/important-longterm`

Notable bugs to consider:

| # | Title |
|---|-------|
| [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) | Unable to perform cdktf diff with multiple stacks (inter-stack deps) |
| [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662) | Cross Stack Reference Not Working with Modules |
| [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976) | Cross stack dependencies fail within wrapper constructs |
| [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) | [Python] Testing.synth_scope is broken |
| [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | Unit testing - toHaveResource() not working |
| [#3532](https://github.com/hashicorp/terraform-cdk/issues/3532) | lifecycle: replaceTriggeredBy should not be a string interpolation |
| [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538) | Testing: fullSynth generated incorrect stack with incoming cross-stack references |
| [#3641](https://github.com/hashicorp/terraform-cdk/issues/3641) | Prebuilt binary missing for platform linux |
| [#2919](https://github.com/hashicorp/terraform-cdk/issues/2919) | terraform variables passed through --var flag and inter-stack dependencies don't interface nicely |
| [#2877](https://github.com/hashicorp/terraform-cdk/issues/2877) | Inconsistent behaviour with variables from Terraform Cloud |

### Convert (HCL) Bugs

| # | Title |
|---|-------|
| [#2641](https://github.com/hashicorp/terraform-cdk/issues/2641) | Convert breaking long lines into multiple causes compilation issues in python |
| [#2800](https://github.com/hashicorp/terraform-cdk/issues/2800) | Convert: Nested named structs are not properly addressed (JSII upstream issue) |
| [#2820](https://github.com/hashicorp/terraform-cdk/issues/2820) | Convert: Type Coercion adds extra cast due to race condition |
| [#2824](https://github.com/hashicorp/terraform-cdk/issues/2824) | Convert: Golang has wrong casing (lower case letters for attributes) |
| [#2910](https://github.com/hashicorp/terraform-cdk/issues/2910) | hcl2cdk: getExpressionAst fails with regex strings due to escaping |
| [#2912](https://github.com/hashicorp/terraform-cdk/issues/2912) | hcl2cdk: produces incorrect typescript with mix of quoted and unquoted values |
| [#3674](https://github.com/hashicorp/terraform-cdk/issues/3674) | `cdktf convert` mangles string interpolation |

## Files Saved for Analysis

```
./issue-analysis/
├── all-open-issues.json              # All 380 open issues
├── label-summary.json                # Label distribution
├── priority-important-soon.json      # 4 highest priority issues
├── priority-important-longterm.json  # 113 important-longterm issues
├── priority-backlog.json             # 98 backlog issues
├── priority-longterm-summary.json    # Summary view
├── priority-bugs.json                # Bugs with important-longterm label
├── priority-cli.json                 # CLI-related priority issues
└── priority-core.json                # Core library priority issues
```

---

## Language-Specific vs Core Issues

**29 total language-specific issues** across all open issues (labeled `language/*`).

| Language | Count |
|----------|-------|
| Python | 14 |
| Go | 9 |
| C# | 7 |
| Java | 4 |
| TypeScript | 2 |

### Language-Specific Issues in Priority Lists

**Python:**
| # | Title | Priority |
|---|-------|----------|
| [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) | [Python] Testing.synth_scope is broken | important-longterm |
| [#2641](https://github.com/hashicorp/terraform-cdk/issues/2641) | Convert breaking long lines causes compilation issues in python | important-longterm |
| [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) | cdktf tries to use pipenv even tho removed from cdktf.json | backlog |

**Go:**
| # | Title | Priority |
|---|-------|----------|
| [#2824](https://github.com/hashicorp/terraform-cdk/issues/2824) | Convert: Golang has wrong casing (lower case letters for attributes) | important-longterm |
| [#728](https://github.com/hashicorp/terraform-cdk/issues/728) | fallback to hashicorp namespace if none is passed in go provider generation | important-longterm |
| [#3546](https://github.com/hashicorp/terraform-cdk/issues/3546) | ReplaceTriggeredBy: Still not working in Golang | important-longterm |

**C#:**
| # | Title | Priority |
|---|-------|----------|
| [#1479](https://github.com/hashicorp/terraform-cdk/issues/1479) | Warnings the first time synthesizing C# projects | important-longterm |
| [#1898](https://github.com/hashicorp/terraform-cdk/issues/1898) | Azurerm first experience with c# dotnet and typescript | important-longterm |

**Java:**
| # | Title | Priority |
|---|-------|----------|
| [#2340](https://github.com/hashicorp/terraform-cdk/issues/2340) | Java, missing required field error is unclear | important-longterm |

### Core Issues (Language-Agnostic)

All other issues in this document are **core issues** affecting all languages:
- Cross-stack dependencies ([#2157](https://github.com/hashicorp/terraform-cdk/issues/2157), [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662), [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976))
- CLI bugs ([#3640](https://github.com/hashicorp/terraform-cdk/issues/3640), [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698), [#3641](https://github.com/hashicorp/terraform-cdk/issues/3641))
- HCL synth issues ([#2910](https://github.com/hashicorp/terraform-cdk/issues/2910), [#2912](https://github.com/hashicorp/terraform-cdk/issues/2912), [#3674](https://github.com/hashicorp/terraform-cdk/issues/3674))
- Testing framework ([#1850](https://github.com/hashicorp/terraform-cdk/issues/1850), [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538))

---

## Recommendations

### Must Migrate (High Priority)
1. Both `priority/important-soon` bugs
2. All cross-stack dependency bugs ([#2157](https://github.com/hashicorp/terraform-cdk/issues/2157), [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662), [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976))
3. Testing framework bugs ([#1850](https://github.com/hashicorp/terraform-cdk/issues/1850), [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871), [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538))
4. Critical CLI bugs

### Consider Migrating
1. `priority/important-longterm` bugs that affect core functionality
2. Feature requests with `help wanted` or `good first issue` labels
3. Issues related to provider generation

### May Not Need Migration
1. Issues labeled `terraform cloud` (if not supporting TFC)
2. Issues with `waiting-for-3rd-party-fix`
3. Issues related to `upstream/jsii` that are JSII's responsibility
