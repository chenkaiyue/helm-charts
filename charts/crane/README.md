# Crane
## TL;DR

```console
helm repo add crane https://gocrane.github.io/helm-charts
helm repo update

helm install crane -n crane-system --create-namespace crane/crane
```

## Introduction

This chart bootstraps Crane Components on a Kubernetes cluster using the Helm package manager.

## Prerequisites

* Kubernetes 1.18+
* Helm 3+

## Get Repo Info

```console
helm repo add crane https://gocrane.github.io/helm-charts
helm repo update
```

See [helm repo](https://helm.sh/docs/helm/helm_repo/) for command documentation.

## Install Chart

```console
helm install crane -n crane-system --create-namespace crane/crane
```

See [configuration](#configuration) below.

See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation.

## Uninstall Chart

```console
helm uninstall crane -n crane-system
```

This removes all the Kubernetes components associated with the chart and deletes the release.

See [helm uninstall](https://helm.sh/docs/helm/helm_uninstall/) for command documentation.

## Configuration

The following table lists the configurable parameters of the Crane chart and their default values.

| Parameter                                                  | Description                               | Default                                         |
|:-----------------------------------------------------------|:------------------------------------------|:------------------------------------------------|
| `craned.image.repository`                                  | Image name of Craned                      | `docker.io/gocrane/craned`                |
| `craned.image.tag`                                         | Image tag of Craned. Optional, given app version of Helm chart is used by default | `` |
| `craned.image.pullPolicy`                                  | Image pullPolicy of Craned | `IfNotPresent` |
| `craned.replicaCount`                                      | Replica count of Craned | `1` |
| `craned.containerArgs`                                     | Container's command line arguments to pass to Craned | `{ "prometheus-address": "http://prometheus-server.crane-system.svc.cluster.local:8080", "feature-gates": "Analysis=true,TimeSeriesPrediction=true,Autoscaling=true", "v": "2"}` |
| `craned.podAnnotations`                                    | Pod annotations  of Craned | `{}` |
| `craned.resources`                                         | Pod resources of Craned | `{}` |
| `craned.nodeSelector`                                      | Node selectors of Craned deployment| `{}` |
| `craned.tolerations`                                       | Tolerations of Craned deployment | `{}` |
| `craned.affinity`                                          | Affinity of Craned deployment | `{}` |
| `craned.nodeSelector`                                      | Node selectors of Craned | `{}` |
| `metricAdapter.image.repository`                           | Image name of MetricAdapter                      | `docker.io/gocrane/metric-adapter`                |
| `metricAdapter.image.tag`                                  | Image tag of MetricAdapter. Optional, given app version of Helm chart is used by default | `` |
| `metricAdapter.image.pullPolicy`                           | Image pullPolicy of MetricAdapter | `IfNotPresent` |
| `metricAdapter.replicaCount`                               | Replica count of MetricAdapter | `1` |
| `metricAdapter.containerArgs`                              | Container's command line arguments to pass to MetricAdapter | `{ "secure-port": "6443", "alsologtostderr": "true", "v": "", "api-qps": "300", "api-burst": "400"}` |
| `metricAdapter.remoteAdapterEnabled`                       | Enable remote adapter feature to MetricAdapter | `false` |
| `metricAdapter.remoteAdapterArgs`                          | Remote adapter command line arguments to pass to MetricAdapter | `{ "remote-adapter-service-namespace": "", "remote-adapter-service-name": "", "remote-adapter-service-port": ""}` |
| `metricAdapter.podAnnotations`                             | Pod annotations  of MetricAdapter | `{}` |
| `metricAdapter.resources`                                  | Pod resources of MetricAdapter | `{}` |
| `metricAdapter.nodeSelector`                               | Node selectors of MetricAdapter deployment| `{}` |
| `metricAdapter.tolerations`                                | Tolerations of MetricAdapter deployment | `{}` |
| `metricAdapter.affinity`                                   | Affinity of MetricAdapter deployment | `{}` |
| `metricAdapter.nodeSelector`                               | Node selectors of MetricAdapter | `{}` |