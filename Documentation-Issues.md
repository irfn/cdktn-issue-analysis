# Documentation Issues

## Summary

**65 documentation issues** total.

| Priority | Count |
|----------|-------|
| important-soon | 2 |
| important-longterm | 29 |
| backlog | 21 |
| none | 13 |

**Note:** Many of these reference HashiCorp's developer.hashicorp.com site. For cdk-terrain, these would need to be adapted to new documentation infrastructure.

---

## Highest Priority (important-soon)

| # | Title |
|---|-------|
| [#2535](https://github.com/hashicorp/terraform-cdk/issues/2535) | Passing backend config through `TerraformVariable`s is not supported by Terraform |
| [#3042](https://github.com/hashicorp/terraform-cdk/issues/3042) | Documentation: Constructs page scope text not in alignment with code |

---

## Important-Longterm by Category

### Core Concepts & Getting Started

| # | Title |
|---|-------|
| [#798](https://github.com/hashicorp/terraform-cdk/issues/798) | Reduce/document differences between cdktf synth and running app directly |
| [#1406](https://github.com/hashicorp/terraform-cdk/issues/1406) | Docs: Add note about `synth` being common term in CDK ecosystem |
| [#2109](https://github.com/hashicorp/terraform-cdk/issues/2109) | Explain synth vs execution time on Tokens page |
| [#2867](https://github.com/hashicorp/terraform-cdk/issues/2867) | (Concepts): new page to document Operators usage |

### Modules & Providers

| # | Title |
|---|-------|
| [#304](https://github.com/hashicorp/terraform-cdk/issues/304) | DOC: is there any API/DOC for providers maintainer to support terraform-cdk? |
| [#956](https://github.com/hashicorp/terraform-cdk/issues/956) | Add specific example for using private Terraform modules to docs |
| [#1443](https://github.com/hashicorp/terraform-cdk/issues/1443) | Document data access for modules |
| [#1631](https://github.com/hashicorp/terraform-cdk/issues/1631) | Make TerraformHclModule more beginner friendly |
| [#2072](https://github.com/hashicorp/terraform-cdk/issues/2072) | Create examples using modules |
| [#2613](https://github.com/hashicorp/terraform-cdk/issues/2613) | Module outputs may require "Token typecasting" when passed into Terraform functions |

### Variables, Tokens & Configuration

| # | Title |
|---|-------|
| [#2114](https://github.com/hashicorp/terraform-cdk/issues/2114) | Improve TerraformVariable docs to mention stringValue, numberValue, etc |
| [#2511](https://github.com/hashicorp/terraform-cdk/issues/2511) | Document how to use escape hatch with lists |
| [#2515](https://github.com/hashicorp/terraform-cdk/issues/2515) | Document how to pass a `provider` to a resource |
| [#2548](https://github.com/hashicorp/terraform-cdk/issues/2548) | Improve list token access error message |

### Stacks & Dependencies

| # | Title |
|---|-------|
| [#1829](https://github.com/hashicorp/terraform-cdk/issues/1829) | Make clear that `Stack.dependsOn` does not create dependency between stacks (`addDependency` does) |
| [#2235](https://github.com/hashicorp/terraform-cdk/issues/2235) | Inconsistent UX for multi-stack cdktf commands |
| [#2334](https://github.com/hashicorp/terraform-cdk/issues/2334) | Inconsistent behaviour of `dependsOn` if set via initial resource config vs. via `resource.dependsOn` |

### Backends & State

| # | Title |
|---|-------|
| [#1216](https://github.com/hashicorp/terraform-cdk/issues/1216) | Docs need (security) guidance around `.terraform.lock.hcl` |
| [#1268](https://github.com/hashicorp/terraform-cdk/issues/1268) | API docs: Add docs to Terraform backends |

### Import & Migration

| # | Title |
|---|-------|
| [#526](https://github.com/hashicorp/terraform-cdk/issues/526) | Improve cdktf upgrade documentation |
| [#1313](https://github.com/hashicorp/terraform-cdk/issues/1313) | Add more documentation about how to work with existing resources (import/alteration) |
| [#3615](https://github.com/hashicorp/terraform-cdk/issues/3615) | Running terraform --reconfigure --upgrade through cdktf |

### Team Collaboration & Governance

| # | Title |
|---|-------|
| [#918](https://github.com/hashicorp/terraform-cdk/issues/918) | How multiple team members can use terraform CDKTF Project in a shared way |
| [#2710](https://github.com/hashicorp/terraform-cdk/issues/2710) | Guide: How to use custom constructs to solve governance problems |

### Assets

| # | Title |
|---|-------|
| [#2711](https://github.com/hashicorp/terraform-cdk/issues/2711) | Assets: Add documentation around TerraformCachedAsset |

### Testing

| # | Title |
|---|-------|
| [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) | [Python] Testing.synth_scope is broken |

### Examples & Tutorials

| # | Title |
|---|-------|
| [#2071](https://github.com/hashicorp/terraform-cdk/issues/2071) | Use DataSources in the examples where possible |
| [#3071](https://github.com/hashicorp/terraform-cdk/issues/3071) | Missing import in the example of using `cdktf` for `typescript` |
| [#3095](https://github.com/hashicorp/terraform-cdk/issues/3095) | Display correct data format inside document |

---

## Backlog (21 issues)

Lower priority documentation issues - review for relevance to cdk-terrain.

| # | Title |
|---|-------|
| [#1620](https://github.com/hashicorp/terraform-cdk/issues/1620) | cdktf get - jsii compilation failed - using terraform-google-modules/iam/google |
| [#2638](https://github.com/hashicorp/terraform-cdk/issues/2638) | Converting from Terraform, we need the provider to be explicitly stated |
| [#3032](https://github.com/hashicorp/terraform-cdk/issues/3032) | [Notice] Provider documentation on registry.terraform.io |

---

## Language-Specific vs Core Issues

### Language-Specific Documentation Issues

| # | Title | Language |
|---|-------|----------|
| [#432](https://github.com/hashicorp/terraform-cdk/issues/432) | More examples using inheritance in Python for CDKTF | Python |
| [#2514](https://github.com/hashicorp/terraform-cdk/issues/2514) | Improve Golang template & docs to include `defer jsii.Close()` cleanup call | Go |
| [#2578](https://github.com/hashicorp/terraform-cdk/issues/2578) | Complex variables snippet not translated in `variables-and-outputs.mdx` | Python, Java, C# |
| [#3436](https://github.com/hashicorp/terraform-cdk/issues/3436) | cdktf-go: Error when following the examples in the documentation | Go |
| [#2871](https://github.com/hashicorp/terraform-cdk/issues/2871) | [Python] Testing.synth_scope is broken | Python |
| [#3071](https://github.com/hashicorp/terraform-cdk/issues/3071) | Missing import in the example of using `cdktf` for `typescript` | TypeScript |

### Core Documentation Issues (Language-Agnostic)

All other documentation issues are **core docs** applicable to all languages:
- Core concepts ([#798](https://github.com/hashicorp/terraform-cdk/issues/798), [#1406](https://github.com/hashicorp/terraform-cdk/issues/1406), [#2109](https://github.com/hashicorp/terraform-cdk/issues/2109), [#2867](https://github.com/hashicorp/terraform-cdk/issues/2867))
- Modules & Providers ([#304](https://github.com/hashicorp/terraform-cdk/issues/304), [#956](https://github.com/hashicorp/terraform-cdk/issues/956), [#1443](https://github.com/hashicorp/terraform-cdk/issues/1443), [#1631](https://github.com/hashicorp/terraform-cdk/issues/1631), [#2072](https://github.com/hashicorp/terraform-cdk/issues/2072), [#2613](https://github.com/hashicorp/terraform-cdk/issues/2613))
- Variables & Tokens ([#2114](https://github.com/hashicorp/terraform-cdk/issues/2114), [#2511](https://github.com/hashicorp/terraform-cdk/issues/2511), [#2515](https://github.com/hashicorp/terraform-cdk/issues/2515), [#2548](https://github.com/hashicorp/terraform-cdk/issues/2548))
- Stacks & Dependencies ([#1829](https://github.com/hashicorp/terraform-cdk/issues/1829), [#2235](https://github.com/hashicorp/terraform-cdk/issues/2235), [#2334](https://github.com/hashicorp/terraform-cdk/issues/2334))
- Backends & State ([#1216](https://github.com/hashicorp/terraform-cdk/issues/1216), [#1268](https://github.com/hashicorp/terraform-cdk/issues/1268))

---

## Recommendation

**Migrate:** Core concept docs ([#798](https://github.com/hashicorp/terraform-cdk/issues/798), [#2109](https://github.com/hashicorp/terraform-cdk/issues/2109), [#1829](https://github.com/hashicorp/terraform-cdk/issues/1829), [#2334](https://github.com/hashicorp/terraform-cdk/issues/2334)) - these explain fundamental CDKTF behavior.

**Adapt:** Module/provider docs - will need updates for cdk-terrain's approach.

**Skip:** HashiCorp-specific docs ([#3032](https://github.com/hashicorp/terraform-cdk/issues/3032) registry notice, learn-tutorials tagged issues).
