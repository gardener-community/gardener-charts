# [Gardener](https://gardener.cloud/) charts

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [[Gardener](https://gardener.cloud/) charts](#gardenerhttpsgardenercloud-charts)
    - [How to...](#how-to)
        - [use the released charts?](#use-the-released-charts)
        - [contribute?](#contribute)

<!-- markdown-toc end -->

This is a functional repository collecting and releasing Helm charts required for a Gardener provisioning.
The charts to be released are configured in `chart-releaser-config.yaml` and the releases are generated nightly via a GitHub-Action calling the [gardener-chart-releaser](https://github.com/gardener-community/gardener-chart-releaser).

## How to...

### use the released charts?
You can add the helm repository by
```shell
helm repo add gardener-charts https://gardener-community.github.io/gardener-charts
helm repo update
```
Then, you can work with charts provided by this repository. E.g., you can retrieve information about a chart:
```shell
helm show chart gardener-charts/provider-hcloud
```
which should output something similar to
``` yaml
apiVersion: v2
dependencies:
- condition: controller.enabled
  name: controller
  repository: ""
description: A helmchart for provider-hcloud
name: provider-hcloud
version: v0.5.6
```
Analogously, you can output the rendered chart by:
```shell
helm template ext-provider-hcloud gardener-charts/provider-hcloud --set controller.enabled=true --version=v0.5.5
```

### contribute?
If you feel like a chart is missing in the releases, you can file an issue. If you have proposals for the chart release process, you should checkout the [gardener-chart-releaser](https://github.com/gardener-community/gardener-chart-releaser) repository, and file an issue or pull request there.
