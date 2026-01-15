# Issues Likely Not Needing Migration

*See also: [Maintainers-Priority-Issues.md](./Maintainers-Priority-Issues.md) | [Terraform-Upgrade-Issues.md](./Terraform-Upgrade-Issues.md) | [Documentation-Issues.md](./Documentation-Issues.md) | [Most-Discussed-Issues.md](./Most-Discussed-Issues.md)*

---

## Summary

**~60 issues** identified as likely not needing migration to cdk-terrain.

| Category | Count | Reason |
|----------|-------|--------|
| Stale issues (no updates since mid-2022) | 29 | May be outdated or already fixed |
| Notices (informational) | 3 | Not actual bugs/features |
| HashiCorp-specific | 7 | Terraform Cloud, telemetry, enterprise |
| Needs reproduction/research | 21 | Incomplete - need more info |
| Watch command features | 5 | Feature may be deprecated |
| Telemetry features | 2 | HashiCorp analytics - not relevant |

---

## Stale Issues (Not Updated Since Mid-2022)

29 issues haven't been updated in 2.5+ years. Many may be:
- Already fixed in later releases
- No longer reproducible
- Abandoned feature requests

### Very Stale (2020-2021)

| # | Title | Last Updated |
|---|-------|--------------|
| [#435](https://github.com/hashicorp/terraform-cdk/issues/435) | Making cdktf dynamic | 2021-07-02 |
| [#492](https://github.com/hashicorp/terraform-cdk/issues/492) | Extract common Terraform JSON types | 2022-04-04 |
| [#632](https://github.com/hashicorp/terraform-cdk/issues/632) | Pass input directory as a CLI argument | 2022-02-10 |
| [#653](https://github.com/hashicorp/terraform-cdk/issues/653) | Support remote templates from file:// uris | 2021-11-30 |
| [#660](https://github.com/hashicorp/terraform-cdk/issues/660) | Custom Data Source | 2022-02-10 |
| [#707](https://github.com/hashicorp/terraform-cdk/issues/707) | Providers should know "allowed" values | 2021-11-30 |
| [#708](https://github.com/hashicorp/terraform-cdk/issues/708) | Helper for using local files | 2021-11-29 |
| [#749](https://github.com/hashicorp/terraform-cdk/issues/749) | Create a separate repo for examples | 2021-07-20 |
| [#775](https://github.com/hashicorp/terraform-cdk/issues/775) | Support tainting a resource (or -replace) | 2021-07-02 |
| [#831](https://github.com/hashicorp/terraform-cdk/issues/831) | Document transition between generated and pre-built providers | 2021-07-13 |
| [#838](https://github.com/hashicorp/terraform-cdk/issues/838) | Using CDK to manage multiple Stacks generated separately | 2021-08-09 |
| [#1038](https://github.com/hashicorp/terraform-cdk/issues/1038) | cli: autocomplete error handling | 2022-01-25 |
| [#1090](https://github.com/hashicorp/terraform-cdk/issues/1090) | Synth single stack even when we have multiple stacks | 2021-11-30 |
| [#1103](https://github.com/hashicorp/terraform-cdk/issues/1103) | Design cross-language stack traces | 2022-04-11 |
| [#1124](https://github.com/hashicorp/terraform-cdk/issues/1124) | Test matchers suppress Terraform logs | 2021-10-07 |
| [#1309](https://github.com/hashicorp/terraform-cdk/issues/1309) | Validate Terraform code on synth | 2021-12-02 |
| [#1349](https://github.com/hashicorp/terraform-cdk/issues/1349) | synth should fail if second provider has no alias | 2021-12-02 |
| [#1616](https://github.com/hashicorp/terraform-cdk/issues/1616) | Expose API to identify constructs in tree | 2022-03-29 |
| [#1703](https://github.com/hashicorp/terraform-cdk/issues/1703) | Add library version checks for non-TS languages | 2022-04-08 |

### Likely Fixed Platform Issues

| # | Title | Last Updated | Notes |
|---|-------|--------------|-------|
| [#909](https://github.com/hashicorp/terraform-cdk/issues/909) | Unable to run on M1 with asdf-vm | 2021-09-02 | M1 support improved since then |
| [#1479](https://github.com/hashicorp/terraform-cdk/issues/1479) | Warnings synthesizing C# projects | 2022-02-08 | May be fixed in newer JSII |
| [#1659](https://github.com/hashicorp/terraform-cdk/issues/1659) | Can Not Deref Tags from another Object | 2022-04-19 | Unclear if still relevant |

**Recommendation:** Verify if still reproducible before migrating. Close if no longer relevant.

---

## Notices (Informational Only)

These are announcements, not bugs or feature requests.

| # | Title | Notes |
|---|-------|-------|
| [#2146](https://github.com/hashicorp/terraform-cdk/issues/2146) | [Notice] Moving pre-built providers to `cdktf` org | Historical - already happened |
| [#2160](https://github.com/hashicorp/terraform-cdk/issues/2160) | [Notice] Breaking Change in CDKTF 0.13 | Historical - v0.13 released |
| [#3032](https://github.com/hashicorp/terraform-cdk/issues/3032) | [Notice] Provider documentation on registry.terraform.io | HashiCorp registry specific |

**Recommendation:** Do not migrate. These are historical announcements.

---

## HashiCorp-Specific Issues

Issues specific to HashiCorp products/services that may not apply to cdk-terrain.

### Terraform Cloud

| # | Title |
|---|-------|
| [#956](https://github.com/hashicorp/terraform-cdk/issues/956) | Add example for private Terraform modules (TFC/enterprise) |
| [#1734](https://github.com/hashicorp/terraform-cdk/issues/1734) | Improve init templates (TFC string replacing) |
| [#1874](https://github.com/hashicorp/terraform-cdk/issues/1874) | Create GitHub action for TFC workspaces |
| [#2877](https://github.com/hashicorp/terraform-cdk/issues/2877) | Inconsistent behaviour with variables from Terraform Cloud |
| [#3586](https://github.com/hashicorp/terraform-cdk/issues/3586) | CloudBackend: support TF_CLOUD_ORGANIZATION env var |

### Telemetry (HashiCorp Analytics)

| # | Title |
|---|-------|
| [#841](https://github.com/hashicorp/terraform-cdk/issues/841) | Telemetry does not get sent due to process.exit |
| [#1639](https://github.com/hashicorp/terraform-cdk/issues/1639) | Telemetry: track CLI flags being used |

**Recommendation:** Decide if cdk-terrain will support Terraform Cloud. If not, skip these. Telemetry issues are not relevant unless cdk-terrain implements its own analytics.

---

## Needs Reproduction/Research

Issues that are incomplete or unverified. May not be real bugs.

| # | Title | Status |
|---|-------|--------|
| [#3106](https://github.com/hashicorp/terraform-cdk/issues/3106) | TLS: RuntimeError: Cannot read properties of undefined | needs-reproduction |
| [#3187](https://github.com/hashicorp/terraform-cdk/issues/3187) | cdktf is unable to resolve AWS local credentials | needs-reproduction |
| [#3621](https://github.com/hashicorp/terraform-cdk/issues/3621) | synth --hcl fails to render false, 0, "" | needs-reproduction |
| [#3568](https://github.com/hashicorp/terraform-cdk/issues/3568) | error when using local providers due to incomplete lock file | needs-research |
| [#3825](https://github.com/hashicorp/terraform-cdk/issues/3825) | hashicorp/hcp 0.102.0: Warning during Apply | needs-research |
| [#3870](https://github.com/hashicorp/terraform-cdk/issues/3870) | generated Typescript constructs use non-erasable syntax | needs-research |
| [#880](https://github.com/hashicorp/terraform-cdk/issues/880) | Allow using CLI without having a config file | needs-research |
| [#2228](https://github.com/hashicorp/terraform-cdk/issues/2228) | azurerm: priority field should be required | needs-research |
| [#2435](https://github.com/hashicorp/terraform-cdk/issues/2435) | Add support for no backend | needs-research |
| [#3019](https://github.com/hashicorp/terraform-cdk/issues/3019) | Improvements to C# Ergonomics | needs-research |

**Recommendation:** Attempt to reproduce before migrating. Close if not reproducible.

---

## Watch Command Features

The `cdktf watch` command may be deprecated or low priority for cdk-terrain.

| # | Title | Last Updated |
|---|-------|--------------|
| [#869](https://github.com/hashicorp/terraform-cdk/issues/869) | Watch: Detect changes for Assets outside project dir | 2021-09-02 |
| [#870](https://github.com/hashicorp/terraform-cdk/issues/870) | Watch: Support manual approval | 2021-09-02 |
| [#871](https://github.com/hashicorp/terraform-cdk/issues/871) | Watch: Make use of target language tooling | 2021-09-02 |
| [#1003](https://github.com/hashicorp/terraform-cdk/issues/1003) | Evaluate integrating watch and unit testing | 2021-11-30 |
| [#1105](https://github.com/hashicorp/terraform-cdk/issues/1105) | Plan next revision of `cdktf watch` command | 2022-02-01 |

**Recommendation:** Decide if cdk-terrain will support `watch`. If not, skip these.

---

## Other Low-Priority/Questionable

| # | Title | Reason |
|---|-------|--------|
| [#2201](https://github.com/hashicorp/terraform-cdk/issues/2201) | PowerShell support | Stale (2022-10), low demand |
| [#2143](https://github.com/hashicorp/terraform-cdk/issues/2143) | Unmet peer dependencies for the cli | Stale (2022-10), may be fixed |

---

## Summary by Action

| Action | Count | Notes |
|--------|-------|-------|
| **Do Not Migrate** | ~10 | Notices, telemetry |
| **Verify First** | ~30 | Stale issues, needs-reproduction |
| **Decide on Feature** | ~12 | TFC, watch command |
| **Low Priority** | ~8 | PowerShell, old design docs |
