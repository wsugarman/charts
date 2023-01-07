# Charts
This repository hosts Helm charts created by Will Sugarman ([@wsugarman](https://github.com/wsugarman)). It serves as both a [Helm Chart Repository](https://helm.sh/docs/topics/chart_repository/) and as an [Artifact Hub KEDA Scaler Repository](https://artifacthub.io/docs/topics/repositories/keda-scalers/). The source code for the charts cannot be found here. Instead, charts are automatically synchronized with pull requests from their respective CI GitHub actions:

| Chart                             | Repository                                                   |
|-----------------------------------|--------------------------------------------------------------|
| `durabletask-azurestorage-scaler` | https://github.com/wsugarman/durabletask-azurestorage-scaler |

## Helm Chart Repository
The chart repository is controlled by the [index.yaml](./index.yaml) that details all of the available charts and their versions. As new charts and versions are published, their corresponding archives and provenance files are found in the root folder:
```
./charts/
  |
  |- index.yaml
  |- durabletask-azurestorage-scaler-1.0.0.tgz
  |- durabletask-azurestorage-scaler-1.0.0.tgz.prov
  |- durabletask-azurestorage-scaler-2.0.0.tgz
  |- durabletask-azurestorage-scaler-2.0.0.tgz.prov
  |- ...
```

### Installation
To install any of the Helm charts, the chart repository must be added using [`helm repo add`](https://helm.sh/docs/helm/helm_repo_add/):
```bash
helm repo add wsugarman https://wsugarman.github.io/charts
helm repo update
```

Afterwards, any of the charts in the repository may be installed using [`helm install`](https://helm.sh/docs/helm/helm_install/):
```bash
helm install --namespace keda --create-namespace dtfx-scaler wsugarman/durabletask-azurestorage-scaler
```

## Artifact Hub
The Artifact Hub Scaler repository is found under the [artifacthub](./artifacthub/) folder. Repository information is recorded in the [artifacthub-repo.yml](./artifacthub/artifacthub-repo.yml) while every published scaler version is found in a separate folder:
```
./charts/artifacthub/
  |
  |- artifacthub-repo.yml
  |- durabletask-azurestorage-scaler
      |
      |- 1.0.0
      |   |
      |   |- README.md
      |   |- artifacthub-pkg.yml
      |
      |- 2.0.0
          |
          |- README.md
          |- artifacthub-pkg.yml
```
