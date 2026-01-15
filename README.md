# terraform-cdk Issue Analysis for cdk-terrain Migration

**Source:** https://github.com/hashicorp/terraform-cdk (archived)
**Target:** https://github.com/open-constructs/cdk-terrain
**Analysis Date:** 2026-01-15

---

## Summary

| Metric | Count |
|--------|-------|
| Total Open Issues | 380 |
| Maintainer Prioritized | 215 |
| Documentation Issues | 65 |
| Language-Specific Issues | 29 |
| Core Issues | ~286 |

### Priority Breakdown

| Priority | Count | Action |
|----------|-------|--------|
| `priority/important-soon` | 4 | Migrate immediately |
| `priority/important-longterm` | 113 | Migrate |
| `priority/backlog` | 98 | Review for relevance |
| Unprioritized | 165 | Triage needed |

### Migration Summary (Recommended)

| Tier | Focus Area | Count | Status |
|------|------------|-------|--------|
| **Tier 1** | Critical/Blocking | 4 | Migrate immediately |
| **Tier 2** | Core Functionality | 10 | High priority |
| **Tier 3** | Important Longterm | 7+ | Medium priority |
| **Tier 4** | Backlog | ~50 | Lower priority |
| **Skip** | Stale/Not Needed | ~60 | Verify or skip |

### Language Distribution

| Language | Count | Top Issue |
|----------|-------|-----------|
| Python | 14 | [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) - pipenv bug (15 comments) |
| Go | 9 | [#3546](https://github.com/hashicorp/terraform-cdk/issues/3546) - replaceTriggeredBy broken |
| C# | 7 | [#3916](https://github.com/hashicorp/terraform-cdk/issues/3916) - .NET 9 upgrade |
| Java | 4 | [#2340](https://github.com/hashicorp/terraform-cdk/issues/2340) - unclear error messages |
| TypeScript | 2 | [#1660](https://github.com/hashicorp/terraform-cdk/issues/1660) - ESM support (9 comments) |

---

## Terraform Version Compatibility

### Current State (CDKTF v0.21.0)

| Version | Status |
|---------|--------|
| **CDKTF Default** | Terraform 1.6.5 |
| **CDKTF Tested** | 1.5.5, 1.6.5 |
| **CDKTF Available** | 1.1.9 - 1.6.5 |
| **Latest Terraform** | v1.14.3 (Dec 2025) |
| **Version Gap** | 8 major versions behind (1.7 - 1.14) |

### Missing Terraform Features

| TF Version | Feature | Issue |
|------------|---------|-------|
| 1.7 | `removed` block for orphan resources | [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) |
| 1.8 | Provider functions | [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) |
| 1.10 | Ephemeral resources | [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) |
| - | OpenTofu compatibility | [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) |

### Upgrade-Related Issues

See [Terraform-Upgrade-Issues.md](./Terraform-Upgrade-Issues.md) for full details.

**Critical blockers:**
- [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) - Provider generation fails on CDKTF >0.20.1
- [#2437](https://github.com/hashicorp/terraform-cdk/issues/2437) - cdktf provider upgrade issues
- [#2191](https://github.com/hashicorp/terraform-cdk/issues/2191) - Pre-built provider version mismatch detection

**For cdk-terrain:** Closing this version gap should be a priority to ensure users can leverage modern Terraform/OpenTofu features.

---

## Analysis Documents

### [Maintainers-Priority-Issues.md](./Maintainers-Priority-Issues.md)

Issues prioritized by the original HashiCorp maintainers.

**Key findings:**
- 2 critical bugs marked `important-soon`
- 113 issues marked `important-longterm` across CLI, Core, Providers, Convert, Testing, Modules
- Cross-stack dependency bugs are a major theme

**Top issues to migrate:**
- [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) - punycode deprecation warning
- [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) - HCL synth remote config bug
- [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) - cdktf diff with multi-stack deps
- [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662) - Cross Stack Reference with Modules

---

### [Terraform-Upgrade-Issues.md](./Terraform-Upgrade-Issues.md)

Issues related to Terraform version compatibility and upgrades.

**Key findings:**
- 4 missing Terraform features (1.7, 1.8, 1.10)
- OpenTofu support requested
- Provider upgrade workflow has bugs

**Critical for cdk-terrain:**
- [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) - OpenTofu support (strategic for fork)
- [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) - Provider functions (Terraform 1.8)
- [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) - Ephemeral resources (Terraform 1.10)
- [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) - Provider generation fails >0.20.1

---

### [Documentation-Issues.md](./Documentation-Issues.md)

Documentation gaps and improvements.

**Key findings:**
- 65 total documentation issues
- Many reference HashiCorp's developer.hashicorp.com (will need new docs infrastructure)
- Core concept docs are valuable to migrate

**Worth migrating:**
- [#798](https://github.com/hashicorp/terraform-cdk/issues/798) - synth vs running app directly
- [#2109](https://github.com/hashicorp/terraform-cdk/issues/2109) - synth vs execution time on Tokens
- [#1829](https://github.com/hashicorp/terraform-cdk/issues/1829) - Stack.dependsOn vs addDependency
- [#2334](https://github.com/hashicorp/terraform-cdk/issues/2334) - dependsOn behavior inconsistency

**Skip:**
- HashiCorp-specific docs ([#3032](https://github.com/hashicorp/terraform-cdk/issues/3032) registry notice)
- learn-tutorials tagged issues

---

### [Most-Discussed-Issues.md](./Most-Discussed-Issues.md)

Issues with highest community engagement (by comment count).

**Key findings:**
- Top issues have 12-17 comments each
- Programmatic API and terraform.workspace are most requested (17 comments each)
- Python experience is a recurring pain point

**Themes:**
1. **Programmatic API** ([#237](https://github.com/hashicorp/terraform-cdk/issues/237), [#682](https://github.com/hashicorp/terraform-cdk/issues/682))
2. **Multi-stack workflows** ([#294](https://github.com/hashicorp/terraform-cdk/issues/294), [#3206](https://github.com/hashicorp/terraform-cdk/issues/3206), [#838](https://github.com/hashicorp/terraform-cdk/issues/838))
3. **Testing** ([#1850](https://github.com/hashicorp/terraform-cdk/issues/1850), [#1093](https://github.com/hashicorp/terraform-cdk/issues/1093))
4. **Python experience** ([#3753](https://github.com/hashicorp/terraform-cdk/issues/3753), [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321), [#2835](https://github.com/hashicorp/terraform-cdk/issues/2835))
5. **Token handling** ([#1641](https://github.com/hashicorp/terraform-cdk/issues/1641), [#1528](https://github.com/hashicorp/terraform-cdk/issues/1528))
6. **Higher-level abstractions** ([#1686](https://github.com/hashicorp/terraform-cdk/issues/1686), [#231](https://github.com/hashicorp/terraform-cdk/issues/231))

---

## Migration Recommendations

### Tier 1: Critical (Migrate Immediately)

Issues blocking users or strategically important for the fork.

| # | Title | Reason | Comments |
|---|-------|--------|----------|
| [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | punycode deprecation warning | `important-soon` - Affects all Node.js 21+ users | 9 |
| [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | HCL synth remote config bug | `important-soon` - Broken functionality | - |
| [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) | OpenTofu support | **Strategic** - Key differentiator for fork | - |
| [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) | Provider generation fails >0.20.1 | **Blocking** - Users can't generate providers | - |

### Tier 2: High Priority (Core Functionality)

Issues affecting core workflows and developer experience.

| # | Title | Reason | Comments |
|---|-------|--------|----------|
| [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) | Provider functions support | TF 1.8 feature - Version gap | - |
| [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) | Ephemeral resources support | TF 1.10 feature - Version gap | - |
| [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) | `removed` block support | TF 1.7 feature - Version gap | - |
| [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) | Multi-stack diff broken | Cross-stack bug - Major pain point | - |
| [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662) | Cross-stack refs with modules | Cross-stack bug | - |
| [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976) | Cross-stack deps in wrappers | Cross-stack bug | - |
| [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | toHaveResource() broken | Testing framework - 14 comments | 14 |
| [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538) | fullSynth cross-stack bug | Testing framework | - |
| [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) | Python Testing.synth_scope broken | Testing + Python | - |
| [#237](https://github.com/hashicorp/terraform-cdk/issues/237) | Programmatic API | 17 comments, `important-longterm` | 17 |

### Tier 3: Medium Priority (Important Longterm)

Significant issues but not blocking core functionality.

| # | Title | Reason | Comments |
|---|-------|--------|----------|
| [#376](https://github.com/hashicorp/terraform-cdk/issues/376) | terraform.workspace equivalent | 17 comments - High demand | 17 |
| [#294](https://github.com/hashicorp/terraform-cdk/issues/294) | State locking handling | 12 comments, `important-longterm` | 12 |
| [#2437](https://github.com/hashicorp/terraform-cdk/issues/2437) | Provider upgrade workflow bugs | Provider management | - |
| [#682](https://github.com/hashicorp/terraform-cdk/issues/682) | Lifecycle hooks | 7 comments, `important-longterm` | 7 |
| [#1686](https://github.com/hashicorp/terraform-cdk/issues/1686) | Higher-level Constructs | 13 comments - Ecosystem growth | 13 |
| [#3532](https://github.com/hashicorp/terraform-cdk/issues/3532) | replaceTriggeredBy bug | Lifecycle feature broken | - |
| [#3641](https://github.com/hashicorp/terraform-cdk/issues/3641) | Linux prebuilt binary missing | Platform support | 7 |

### Tier 4: Lower Priority (Backlog)

Worth migrating but not urgent.

- `priority/backlog` bugs with >5 comments
- Convert (HCL) bugs affecting specific languages
- Feature requests with `help wanted` or `good first issue` labels
- Python experience issues ([#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) pipenv - 15 comments, [#3753](https://github.com/hashicorp/terraform-cdk/issues/3753) slow imports)

### Skip or Verify First

See [Issues-Likely-Not-Needed.md](./Issues-Likely-Not-Needed.md) for detailed analysis (~60 issues).

| Category | Count | Action |
|----------|-------|--------|
| Stale issues (no updates since 2022) | 29 | Verify reproducibility first |
| Notices (informational) | 3 | Do not migrate |
| HashiCorp-specific (TFC, telemetry) | 9 | Skip unless supporting TFC |
| Needs reproduction | 21 | Verify before migrating |
| Watch command features | 5 | Decide on feature support |

---

## Raw Data Files

```
./issue-analysis/
├── README.md                         # This file
├── Maintainers-Priority-Issues.md    # Priority-labeled issues
├── Terraform-Upgrade-Issues.md       # Upgrade/version issues
├── Documentation-Issues.md           # Documentation issues
├── Most-Discussed-Issues.md          # High-comment issues
├── Issues-Likely-Not-Needed.md       # Issues to skip or verify
└── data/
    ├── all-open-issues.json          # All 380 open issues (raw)
    ├── label-summary.json            # Label distribution
    ├── priority-important-soon.json  # 4 highest priority
    ├── priority-important-longterm.json # 113 important-longterm
    ├── priority-backlog.json         # 98 backlog
    ├── priority-longterm-summary.json # Summary view
    ├── priority-bugs.json            # Bugs with priority label
    ├── priority-cli.json             # CLI-related priority
    ├── priority-core.json            # Core library priority
    ├── most-discussed-issues.json    # Top 50 by comments
    ├── language-specific-issues.json # Language-labeled issues
    ├── docs-summary.json             # Documentation issues
    └── upgrade-issues.json           # Upgrade-related issues
```

---

## Next Steps

### Immediate Actions
1. **Create Tier 1 issues in cdk-terrain** - 4 critical/blocking issues
2. **Address Terraform version gap** - Support TF 1.7+ features (removed block, provider functions, ephemeral resources)
3. **Implement OpenTofu support** ([#3593](https://github.com/hashicorp/terraform-cdk/issues/3593)) - Strategic differentiator for the fork

### Short-term
4. **Fix cross-stack dependency bugs** ([#2157](https://github.com/hashicorp/terraform-cdk/issues/2157), [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662), [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976)) - Major pain point
5. **Fix testing framework** ([#1850](https://github.com/hashicorp/terraform-cdk/issues/1850), [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538)) - Developer experience
6. **Set up documentation infrastructure** for migrated docs

### Medium-term
7. **Triage unprioritized issues** (165 issues) for relevance
8. **Coordinate with JSII upstream** on blocked issues ([#2800](https://github.com/hashicorp/terraform-cdk/issues/2800))
9. **Decide on Terraform Cloud support** - Affects ~7 issues

### Notes
- Total recommended migrations: ~70 issues (Tier 1-3)
- ~60 issues can likely be skipped or need verification first
- ~165 unprioritized issues need triage
