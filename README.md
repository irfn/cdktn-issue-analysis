# terraform-cdk Issue Analysis for cdk-terrain Migration

**Source:** https://github.com/hashicorp/terraform-cdk (archived)

**Target:** https://github.com/open-constructs/cdk-terrain

**Analysis Date:** 2026-01-15

---

## Summary

| Metric | Count |
|--------|-------|
| Total Open Issues | 380 |
| Total Open PRs | 12 |
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
| **Tier 1** | Critical/Blocking | 3 | Migrate immediately |
| **Tier 2** | TF Version Gap (1.7-1.10) | 3 | **High priority** |
| **Tier 3** | Core Functionality | 7 | High priority |
| **Tier 4** | Important Longterm | 8+ | Medium priority |
| **Tier 5** | Backlog | ~50 | Lower priority |
| **Skip** | Stale/Not Needed | ~60 | Verify or skip |

### Open PRs Summary

| Category | Count | Key PRs |
|----------|-------|---------|
| Fixes Priority Issues | 4 | [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920) (important-soon), [#3928](https://github.com/hashicorp/terraform-cdk/pull/3928), [#3925](https://github.com/hashicorp/terraform-cdk/pull/3925), [#3934](https://github.com/hashicorp/terraform-cdk/pull/3934) |
| Other Bug Fixes | 4 | StringMapMap, Go 1.24, hclOutput, DEP0044 |
| Maintenance/Deps | 3 | Copyright headers, Security CVE, GitHub Actions |
| Documentation | 1 | Conditional example |

See [Open-PRs-Analysis.md](./Open-PRs-Analysis.md) for full details.

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

### [Top-10-Issues-Analysis.md](./Top-10-Issues-Analysis.md)

Deep-dive analysis of the 10 highest priority issues.

**Key findings:**
- 1 issue has ready PR ([#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) → [PR #3920](https://github.com/hashicorp/terraform-cdk/pull/3920))
- 3 issues are Terraform version gap features (TF 1.7, 1.8, 1.10) - **high priority**
- [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) is blocking provider generation

**Implementation phases:**
1. **Critical** - [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698), [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640), [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803)
2. **TF Version Gap** - [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) (TF 1.7), [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) (TF 1.8), [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) (TF 1.10)
3. **Core Improvements** - [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) (multi-stack), [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) (testing)
4. **Future** - [#237](https://github.com/hashicorp/terraform-cdk/issues/237) (programmatic API), [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) (OpenTofu)

---

### [Open-PRs-Analysis.md](./Open-PRs-Analysis.md)

Open PRs awaiting merge at time of archival.

**Key findings:**
- 12 total open PRs
- 4 PRs fix issues in our priority lists
- PR [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920) fixes important-soon issue [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698)
- PR [#3925](https://github.com/hashicorp/terraform-cdk/pull/3925) fixes 15-comment pipenv issue + adds Poetry/UV support

**Immediate actions:**
- Cherry-pick/merge PRs [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920), [#3928](https://github.com/hashicorp/terraform-cdk/pull/3928), [#3925](https://github.com/hashicorp/terraform-cdk/pull/3925), [#3934](https://github.com/hashicorp/terraform-cdk/pull/3934)
- Review security fix [#3946](https://github.com/hashicorp/terraform-cdk/pull/3946)

---

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

Issues blocking users or affecting all users.

| # | Title | Reason | Comments |
|---|-------|--------|----------|
| [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | punycode deprecation warning | `important-soon` - Affects all Node.js 21+ users | 9 |
| [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | HCL synth remote config bug | `important-soon` - Has PR ready | - |
| [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) | Provider generation fails >0.20.1 | **Blocking** - Users can't generate providers | - |

### Tier 2: High Priority (Terraform Version Gap)

Close the 8-version gap (TF 1.7-1.14). **Strategic priority for cdk-terrain.**

| # | Title | Reason | Comments |
|---|-------|--------|----------|
| [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) | `removed` block support | TF 1.7 feature | - |
| [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) | Provider functions support | TF 1.8 feature | - |
| [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) | Ephemeral resources support | TF 1.10 feature | - |

### Tier 3: High Priority (Core Functionality)

Issues affecting core workflows and developer experience.

| # | Title | Reason | Comments |
|---|-------|--------|----------|
| [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) | Multi-stack diff broken | Cross-stack bug - Major pain point | - |
| [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662) | Cross-stack refs with modules | Cross-stack bug | - |
| [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976) | Cross-stack deps in wrappers | Cross-stack bug | - |
| [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | toHaveResource() broken | Testing framework - 14 comments | 14 |
| [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538) | fullSynth cross-stack bug | Testing framework | - |
| [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) | Python Testing.synth_scope broken | Testing + Python | - |
| [#237](https://github.com/hashicorp/terraform-cdk/issues/237) | Programmatic API | 17 comments, `important-longterm` | 17 |

### Tier 4: Medium Priority (Important Longterm)

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
| [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) | OpenTofu support | Future consideration | 1 |

### Tier 5: Lower Priority (Backlog)

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
├── Top-10-Issues-Analysis.md         # Deep-dive on top 10 issues
├── Open-PRs-Analysis.md              # Open PRs analysis
├── Maintainers-Priority-Issues.md    # Priority-labeled issues
├── Terraform-Upgrade-Issues.md       # Upgrade/version issues
├── Documentation-Issues.md           # Documentation issues
├── Most-Discussed-Issues.md          # High-comment issues
├── Issues-Likely-Not-Needed.md       # Issues to skip or verify
└── data/
    ├── all-open-issues.json          # All 380 open issues (raw)
    ├── all-open-prs.json             # All 12 open PRs (raw)
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
1. **Merge/cherry-pick priority PRs** - [#3920](https://github.com/hashicorp/terraform-cdk/pull/3920), [#3928](https://github.com/hashicorp/terraform-cdk/pull/3928), [#3925](https://github.com/hashicorp/terraform-cdk/pull/3925), [#3934](https://github.com/hashicorp/terraform-cdk/pull/3934)
2. **Create Tier 1 issues in cdk-terrain** - 3 critical/blocking issues
3. **Fix provider generation** ([#3803](https://github.com/hashicorp/terraform-cdk/issues/3803)) - Users blocked on newer versions

### Short-term (Terraform Version Gap)
4. **Add `removed` block support** ([#3638](https://github.com/hashicorp/terraform-cdk/issues/3638)) - TF 1.7 feature
5. **Add provider functions** ([#3686](https://github.com/hashicorp/terraform-cdk/issues/3686)) - TF 1.8 feature
6. **Add ephemeral resources** ([#3886](https://github.com/hashicorp/terraform-cdk/issues/3886)) - TF 1.10 feature

### Medium-term (Core Improvements)
7. **Fix cross-stack dependency bugs** ([#2157](https://github.com/hashicorp/terraform-cdk/issues/2157), [#2662](https://github.com/hashicorp/terraform-cdk/issues/2662), [#2976](https://github.com/hashicorp/terraform-cdk/issues/2976)) - Major pain point
8. **Fix testing framework** ([#1850](https://github.com/hashicorp/terraform-cdk/issues/1850), [#3538](https://github.com/hashicorp/terraform-cdk/issues/3538)) - Developer experience
9. **Set up documentation infrastructure** for migrated docs

### Long-term
10. **Triage unprioritized issues** (165 issues) for relevance
11. **Coordinate with JSII upstream** on blocked issues ([#2800](https://github.com/hashicorp/terraform-cdk/issues/2800))
12. **Consider OpenTofu support** ([#3593](https://github.com/hashicorp/terraform-cdk/issues/3593)) - After version gap is closed

### Notes
- **4 PRs ready for merge** - Fix priority issues immediately
- **Terraform version gap is strategic priority** - 8 versions behind (TF 1.7-1.14)
- Total recommended migrations: ~70 issues (Tier 1-4)
- ~60 issues can likely be skipped or need verification first
- ~165 unprioritized issues need triage
