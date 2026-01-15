# Terraform Upgrade & Version Compatibility Issues

## Summary

**14 issues** related to Terraform upgrades and version compatibility (excluding docs).

| Category | Count | Key Issues |
|----------|-------|------------|
| Missing Terraform Features | 4 | Provider functions (1.8), ephemeral resources (1.10), OpenTofu |
| Provider Upgrades | 5 | Upgrade bugs, version pinning, generation failures |
| Version Detection | 4 | Peer dependency checks, cross-language version checks |
| Lifecycle/Import | 3 | replaceTriggeredBy bug, import blocks, lifecycle hooks |
| Framework Upgrades | 2 | .NET 9, Helm provider breaking change |

*Documentation-related upgrade issues tracked in [Documentation-Issues.md](./Documentation-Issues.md)*

**Top 5 for cdk-terrain:**
1. [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) - OpenTofu support (strategic)
2. [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) - Provider functions (TF 1.8)
3. [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) - Ephemeral resources (TF 1.10)
4. [#2437](https://github.com/hashicorp/terraform-cdk/issues/2437) - Provider upgrade bugs
5. [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) - Provider generation fails >0.20.1

---

## Critical: Newer Terraform Features Not Supported

| # | Title | Priority | Notes |
|---|-------|----------|-------|
| [#3886](https://github.com/hashicorp/terraform-cdk/issues/3886) | Support Terraform ephemeral resources | new | Terraform 1.10 feature |
| [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686) | Add support for provider functions | new | Terraform 1.8 feature |
| [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638) | removed block: orphan resources | new | Terraform 1.7 feature |
| [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593) | OpenTofu support | new | Major fork compatibility |

## Provider Upgrade Issues

| # | Title | Priority | Notes |
|---|-------|----------|-------|
| [#2437](https://github.com/hashicorp/terraform-cdk/issues/2437) | cdktf provider upgrade issues | important-longterm | Core upgrade bug |
| [#2230](https://github.com/hashicorp/terraform-cdk/issues/2230) | Support upgrading all providers at once via `cdktf provider upgrade` | important-longterm | UX improvement |
| [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803) | CLI: provider generation fails on versions newer than 0.20.1 | new | Blocking issue |
| [#3488](https://github.com/hashicorp/terraform-cdk/issues/3488) | CDKTF version <0.19 creates duplicates in schema with new Fivetran provider | - | Provider compat |
| [#1762](https://github.com/hashicorp/terraform-cdk/issues/1762) | Provider version gets pinned on synth | awaiting-evidence | Unexpected behavior |

## Version Detection & Compatibility

| # | Title | Priority | Notes |
|---|-------|----------|-------|
| [#2191](https://github.com/hashicorp/terraform-cdk/issues/2191) | Check if pre-built providers peer dependency matches installed cdktf version | important-longterm | Version mismatch detection |
| [#1703](https://github.com/hashicorp/terraform-cdk/issues/1703) | Add library version checks for non-TS languages | awaiting-evidence | Cross-language support |
| [#3759](https://github.com/hashicorp/terraform-cdk/issues/3759) | Support Kotlin build scripts in cdktf library version detection | new | Gradle/Kotlin support |
| [#2746](https://github.com/hashicorp/terraform-cdk/issues/2746) | cdktf Python - Expose version via Python API | important-longterm | Python tooling |

## Lifecycle & Import Features

| # | Title | Priority | Notes |
|---|-------|----------|-------|
| [#3532](https://github.com/hashicorp/terraform-cdk/issues/3532) | lifecycle: replaceTriggeredBy should not be a string interpolation | important-longterm | Bug with workaround |
| [#3527](https://github.com/hashicorp/terraform-cdk/issues/3527) | cdktf-go: CDK for Terraform Go import block | new | Import block support |
| [#3665](https://github.com/hashicorp/terraform-cdk/issues/3665) | Validate referenced objects when generating imports | new | Import validation |
| [#682](https://github.com/hashicorp/terraform-cdk/issues/682) | Lifecycle Hooks | important-longterm | Programmatic hooks |

## Framework Upgrades

| # | Title | Priority | Notes |
|---|-------|----------|-------|
| [#3916](https://github.com/hashicorp/terraform-cdk/issues/3916) | Upgrade .NET framework to 9.0 | new | .NET 9 support |
| [#3908](https://github.com/hashicorp/terraform-cdk/issues/3908) | cdktf-provider-helm: 'id_' error for 'Release' starting version 12.0.0 | new | Breaking change |

---

## Language-Specific vs Core Issues

### Language-Specific Upgrade Issues

| # | Title | Language | Notes |
|---|-------|----------|-------|
| [#2746](https://github.com/hashicorp/terraform-cdk/issues/2746) | cdktf Python - Expose version via Python API | Python | Version tooling |
| [#3527](https://github.com/hashicorp/terraform-cdk/issues/3527) | cdktf-go: CDK for Terraform Go import block | Go | Import block support |
| [#3759](https://github.com/hashicorp/terraform-cdk/issues/3759) | Support Kotlin build scripts in cdktf library version detection | Java/Kotlin | Gradle support |
| [#3916](https://github.com/hashicorp/terraform-cdk/issues/3916) | Upgrade .NET framework to 9.0 | C# | Framework upgrade |
| [#1703](https://github.com/hashicorp/terraform-cdk/issues/1703) | Add library version checks for non-TS languages | Multi | Cross-language |

### Core Issues (Language-Agnostic)

All other issues in this document are **core upgrade issues** affecting all languages:
- Terraform feature support ([#3886](https://github.com/hashicorp/terraform-cdk/issues/3886), [#3686](https://github.com/hashicorp/terraform-cdk/issues/3686), [#3638](https://github.com/hashicorp/terraform-cdk/issues/3638), [#3593](https://github.com/hashicorp/terraform-cdk/issues/3593))
- Provider upgrade mechanics ([#2437](https://github.com/hashicorp/terraform-cdk/issues/2437), [#2230](https://github.com/hashicorp/terraform-cdk/issues/2230), [#3803](https://github.com/hashicorp/terraform-cdk/issues/3803), [#3488](https://github.com/hashicorp/terraform-cdk/issues/3488), [#1762](https://github.com/hashicorp/terraform-cdk/issues/1762))
- Version detection core ([#2191](https://github.com/hashicorp/terraform-cdk/issues/2191))
- Lifecycle/Import core ([#3532](https://github.com/hashicorp/terraform-cdk/issues/3532), [#3665](https://github.com/hashicorp/terraform-cdk/issues/3665), [#682](https://github.com/hashicorp/terraform-cdk/issues/682))
