# Most Discussed Issues

Issues ranked by comment count, indicating community interest and/or complexity.

*See also: [Maintainers-Priority-Issues.md](./Maintainers-Priority-Issues.md) | [Terraform-Upgrade-Issues.md](./Terraform-Upgrade-Issues.md) | [Documentation-Issues.md](./Documentation-Issues.md)*

---

## Summary

**Themes from High Discussion Issues:**
1. **Programmatic API** - Strong demand for CLI/programmatic interaction ([#237](https://github.com/hashicorp/terraform-cdk/issues/237), [#682](https://github.com/hashicorp/terraform-cdk/issues/682))
2. **Multi-stack workflows** - Pain points with parallel deploys, state locking ([#294](https://github.com/hashicorp/terraform-cdk/issues/294), [#3206](https://github.com/hashicorp/terraform-cdk/issues/3206), [#838](https://github.com/hashicorp/terraform-cdk/issues/838))
3. **Testing** - toHaveResource broken, integration testing design ([#1850](https://github.com/hashicorp/terraform-cdk/issues/1850), [#1093](https://github.com/hashicorp/terraform-cdk/issues/1093))
4. **Python experience** - Slow imports, pipenv issues, PyPi size ([#3753](https://github.com/hashicorp/terraform-cdk/issues/3753), [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321), [#2835](https://github.com/hashicorp/terraform-cdk/issues/2835))
5. **Token/Reference handling** - FQN tokens, number attributes ([#1641](https://github.com/hashicorp/terraform-cdk/issues/1641), [#1528](https://github.com/hashicorp/terraform-cdk/issues/1528), [#2658](https://github.com/hashicorp/terraform-cdk/issues/2658))
6. **Higher-level abstractions** - Constructs ecosystem, modules as constructs ([#1686](https://github.com/hashicorp/terraform-cdk/issues/1686), [#231](https://github.com/hashicorp/terraform-cdk/issues/231))

**Must migrate (high discussion + prioritized):**
- [#237](https://github.com/hashicorp/terraform-cdk/issues/237) - Programmatic API (17 comments, important-longterm)
- [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) - Testing bug (14 comments, important-longterm)
- [#294](https://github.com/hashicorp/terraform-cdk/issues/294) - State locking (12 comments, important-longterm)
- [#1641](https://github.com/hashicorp/terraform-cdk/issues/1641) - FQN tokens UX (9 comments, important-longterm)

**Strong community interest (backlog but high discussion):**
- [#376](https://github.com/hashicorp/terraform-cdk/issues/376) - terraform.workspace equivalent (17 comments)
- [#1686](https://github.com/hashicorp/terraform-cdk/issues/1686) - Higher level Constructs (13 comments)
- [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) - Pipenv bug (15 comments)

---

## Top 10 by Discussion Volume

| # | Title | Comments | Priority | Type |
|---|-------|----------|----------|------|
| [#376](https://github.com/hashicorp/terraform-cdk/issues/376) | `terraform.workspace` equivalent | 17 | backlog | enhancement |
| [#237](https://github.com/hashicorp/terraform-cdk/issues/237) | API to interact with terraform cli | 17 | important-longterm | enhancement |
| [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) | cdktf tries to use pipenv even tho I have removed it from cdktf.json | 15 | backlog | bug |
| [#2235](https://github.com/hashicorp/terraform-cdk/issues/2235) | Inconsistent UX for multi-stack cdktf commands | 14 | important-longterm | docs |
| [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | Unit testing - toHaveResource() - found no resources instead | 14 | important-longterm | bug |
| [#1686](https://github.com/hashicorp/terraform-cdk/issues/1686) | Higher level Constructs | 13 | backlog | enhancement |
| [#838](https://github.com/hashicorp/terraform-cdk/issues/838) | Using CDK to manage multiple Stacks generated separately | 13 | backlog | enhancement |
| [#294](https://github.com/hashicorp/terraform-cdk/issues/294) | State locking and how to handle it | 12 | important-longterm | enhancement |
| [#2535](https://github.com/hashicorp/terraform-cdk/issues/2535) | Passing backend config through `TerraformVariable`s | 10 | important-soon | bug |
| [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | DeprecationWarning: The `punycode` module is deprecated | 9 | important-soon | bug |

---

## High Discussion Bugs (non-docs)

| # | Title | Comments | Priority |
|---|-------|----------|----------|
| [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) | cdktf tries to use pipenv even tho removed from cdktf.json | 15 | backlog |
| [#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) | Unit testing - toHaveResource() not working | 14 | important-longterm |
| [#2535](https://github.com/hashicorp/terraform-cdk/issues/2535) | Passing backend config through `TerraformVariable`s | 10 | important-soon |
| [#3640](https://github.com/hashicorp/terraform-cdk/issues/3640) | DeprecationWarning: punycode module deprecated | 9 | important-soon |
| [#1641](https://github.com/hashicorp/terraform-cdk/issues/1641) | Resource FQN tokens aren't resolved in user friendly way | 9 | important-longterm |
| [#1528](https://github.com/hashicorp/terraform-cdk/issues/1528) | Number attributes not synthed as references | 9 | backlog |
| [#3753](https://github.com/hashicorp/terraform-cdk/issues/3753) | Providers of Large Size: Import is very slow in Python | 7 | - |
| [#3641](https://github.com/hashicorp/terraform-cdk/issues/3641) | Prebuilt binary missing for platform linux | 7 | important-longterm |
| [#3621](https://github.com/hashicorp/terraform-cdk/issues/3621) | synth --hcl fails to render false, 0, "" | 7 | - |
| [#3206](https://github.com/hashicorp/terraform-cdk/issues/3206) | One stack failure locks other stacks state in parallel deploy | 7 | - |
| [#705](https://github.com/hashicorp/terraform-cdk/issues/705) | Unable to initialize cdktf project in pycharm with venv | 8 | awaiting-evidence |

## High Discussion Enhancements (non-docs)

| # | Title | Comments | Priority |
|---|-------|----------|----------|
| [#376](https://github.com/hashicorp/terraform-cdk/issues/376) | `terraform.workspace` equivalent | 17 | backlog |
| [#237](https://github.com/hashicorp/terraform-cdk/issues/237) | API to interact with terraform cli | 17 | important-longterm |
| [#1686](https://github.com/hashicorp/terraform-cdk/issues/1686) | Higher level Constructs | 13 | backlog |
| [#838](https://github.com/hashicorp/terraform-cdk/issues/838) | Using CDK to manage multiple Stacks generated separately | 13 | backlog |
| [#294](https://github.com/hashicorp/terraform-cdk/issues/294) | State locking and how to handle it | 12 | important-longterm |
| [#1660](https://github.com/hashicorp/terraform-cdk/issues/1660) | Support ECMAScript modules (ESM) in CDKTF projects | 9 | awaiting-evidence |
| [#231](https://github.com/hashicorp/terraform-cdk/issues/231) | Transform Modules to Constructs | 8 | important-longterm |
| [#1093](https://github.com/hashicorp/terraform-cdk/issues/1093) | Design CDK for Terraform integration testing | 8 | important-longterm |
| [#682](https://github.com/hashicorp/terraform-cdk/issues/682) | Lifecycle Hooks | 7 | important-longterm |
| [#2835](https://github.com/hashicorp/terraform-cdk/issues/2835) | Allow partial PyPi installs for cdktf-cdktf-provider-aws | 6 | awaiting-evidence |

## Pre-built Provider Issues (High Discussion)

| # | Title | Comments | Notes |
|---|-------|----------|-------|
| [#3753](https://github.com/hashicorp/terraform-cdk/issues/3753) | Providers of Large Size: Import is very slow in Python | 7 | Performance |
| [#3929](https://github.com/hashicorp/terraform-cdk/issues/3929) | aws: Error: Pre-built provider information not found | 6 | Recent |
| [#3774](https://github.com/hashicorp/terraform-cdk/issues/3774) | azurerm: AzurermProviderFeatures Value is not an array | 6 | Recent |
| [#2835](https://github.com/hashicorp/terraform-cdk/issues/2835) | Allow partial PyPi installs for cdktf-cdktf-provider-aws | 6 | Size issue |
| [#2160](https://github.com/hashicorp/terraform-cdk/issues/2160) | [Notice] Breaking Change in CDKTF 0.13 | 8 | Historical |

---

## Language-Specific vs Core Issues

### Language-Specific High Discussion Issues

**Python (most discussed language-specific issues):**
| # | Title | Comments |
|---|-------|----------|
| [#2321](https://github.com/hashicorp/terraform-cdk/issues/2321) | cdktf tries to use pipenv even tho removed from cdktf.json | 15 |
| [#432](https://github.com/hashicorp/terraform-cdk/issues/432) | More examples using inheritance in Python | 9 |
| [#705](https://github.com/hashicorp/terraform-cdk/issues/705) | Unable to initialize cdktf project in pycharm with venv | 8 |
| [#3753](https://github.com/hashicorp/terraform-cdk/issues/3753) | Providers of Large Size: Import is very slow in Python | 7 |
| [#2835](https://github.com/hashicorp/terraform-cdk/issues/2835) | Allow partial PyPi installs for cdktf-cdktf-provider-aws | 6 |

**TypeScript:**
| # | Title | Comments |
|---|-------|----------|
| [#1660](https://github.com/hashicorp/terraform-cdk/issues/1660) | Support ECMAScript modules (ESM) in CDKTF projects | 9 |

### Core Issues (Language-Agnostic) - High Discussion

Most highly discussed issues are **core issues** affecting all languages:
- Programmatic API ([#237](https://github.com/hashicorp/terraform-cdk/issues/237) - 17 comments)
- terraform.workspace equivalent ([#376](https://github.com/hashicorp/terraform-cdk/issues/376) - 17 comments)
- State locking ([#294](https://github.com/hashicorp/terraform-cdk/issues/294) - 12 comments)
- Multi-stack UX ([#2235](https://github.com/hashicorp/terraform-cdk/issues/2235) - 14 comments, [#838](https://github.com/hashicorp/terraform-cdk/issues/838) - 13 comments)
- Testing framework ([#1850](https://github.com/hashicorp/terraform-cdk/issues/1850) - 14 comments, [#1093](https://github.com/hashicorp/terraform-cdk/issues/1093) - 8 comments)
- Higher level Constructs ([#1686](https://github.com/hashicorp/terraform-cdk/issues/1686) - 13 comments)
- Token handling ([#1641](https://github.com/hashicorp/terraform-cdk/issues/1641) - 9 comments, [#1528](https://github.com/hashicorp/terraform-cdk/issues/1528) - 9 comments)
