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

### Language Distribution

| Language | Count | Top Issue |
|----------|-------|-----------|
| Python | 14 | [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) - pipenv bug (15 comments) |
| Go | 9 | [#3546](https://github.com/hashicorp/terraform-cdk/issues/3546) - replaceTriggeredBy broken |
| C# | 7 | [#3916](https://github.com/hashicorp/terraform-cdk/issues/3916) - .NET 9 upgrade |
| Java | 4 | [#2340](https://github.com/hashicorp/terraform-cdk/issues/2340) - unclear error messages |
| TypeScript | 2 | [#1660](https://github.com/hashicorp/terraform-cdk/issues/1660) - ESM support (9 comments) |

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

### Must Migrate (High Priority)

| # | Title | Reason |
|---|-------|--------|
| [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | punycode deprecation | important-soon |
| [#3698](https://github.com/hashicorp/terraform-cdk/issues/3698) | HCL synth remote config | important-soon |
| [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) | OpenTofu support | Strategic for fork |
| [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) | Provider functions | TF 1.8 feature gap |
| [#237](https://github.com/hashicorp/terraform-cdk/issues/237) | Programmatic API | 17 comments, important-longterm |
| [#2157](https://github.com/hashicorp/terraform-cdk/issues/2157) | Multi-stack diff | Cross-stack bug |
| [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | toHaveResource broken | 14 comments, testing |

### Consider Migrating

- `priority/important-longterm` bugs affecting core functionality
- Feature requests with `help wanted` or `good first issue` labels
- Provider generation issues
- High-discussion backlog items ([#376](https://github.com/hashicorp/terraform-cdk/issues/376) terraform.workspace - 17 comments)

### May Not Need Migration

- Issues labeled `terraform cloud` (if not supporting TFC)
- Issues with `waiting-for-3rd-party-fix`
- Issues related to `upstream/jsii` (JSII's responsibility)
- HashiCorp-specific documentation

---

## Raw Data Files

```
./issue-analysis/
├── README.md                         # This file
├── Maintainers-Priority-Issues.md    # Priority-labeled issues
├── Terraform-Upgrade-Issues.md       # Upgrade/version issues
├── Documentation-Issues.md           # Documentation issues
├── Most-Discussed-Issues.md          # High-comment issues
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

1. **Create issues in cdk-terrain** for must-migrate items
2. **Set up documentation infrastructure** for migrated docs
3. **Triage unprioritized issues** (165 issues) for relevance
4. **Decide on Terraform Cloud support** (affects 5 issues)
5. **Coordinate with JSII upstream** on blocked issues
