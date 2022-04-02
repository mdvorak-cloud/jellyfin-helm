# Jellyfin Software Media System

This is a helm chart for [Jellyfin](https://github.com/jellyfin/jellyfin/)

## Prerequisites

- Kubernetes 1.19+
- Helm 3+

## Installing the Chart

To install the chart with the release name `jellyfin`:

```shell
helm repo add jellyfin https://mdvorak-cloud.github.io/jellyfin-helm
helm install jellyfin jellyfin/jellyfin
```

## Uninstalling the Chart

To uninstall/delete the `jellyfin` deployment:

```console
helm delete jellyfin
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Sentry chart and their default values.

| Parameter                              | Description                                                                                 | Default               |
|----------------------------------------|---------------------------------------------------------------------------------------------|-----------------------|
| `image.repository`                     | Image repository                                                                            | `jellyfin/jellyfin`   |
| `image.tag`                            | Image tag. Possible values listed [here](https://hub.docker.com/r/jellyfin/jellyfin/tags/). | `latest`              |
| `image.pullPolicy`                     | Image pull policy                                                                           | `IfNotPresent`        |
| `service.type`                         | Kubernetes service type for the jellyfin GUI                                                | `ClusterIP`           |
| `service.port`                         | Kubernetes port where the jellyfin GUI is exposed                                           | `8096`                |
| `service.annotations`                  | Service annotations for the jellyfin GUI                                                    | `{}`                  |
| `service.labels`                       | Custom labels                                                                               | `{}`                  |
| `service.loadBalancerIP`               | Loadbalance IP for the jellyfin GUI                                                         | `{}`                  |
| `service.loadBalancerSourceRanges`     | List of IP CIDRs allowed access to load balancer (if supported)                             | None                  |
| `ingress.enabled`                      | Enables Ingress                                                                             | `false`               |
| `ingress.annotations`                  | Ingress annotations                                                                         | `{}`                  |
| `ingress.labels`                       | Custom labels                                                                               | `{}`                  |
| `ingress.path`                         | Ingress path                                                                                | `/`                   |
| `ingress.hosts`                        | Ingress accepted hostnames                                                                  | `chart-example.local` |
| `ingress.tls`                          | Ingress TLS configuration                                                                   | `[]`                  |
| `persistence.config.enabled`           | Use persistent volume to store configuration data                                           | `false`               |
| `persistence.config.size`              | Size of persistent volume claim                                                             | `1Gi`                 |
| `persistence.config.existingClaim`     | Use an existing PVC to persist data                                                         | `nil`                 |
| `persistence.config.storageClass`      | Type of persistent volume claim                                                             | `-`                   |
| `persistence.config.accessMode`        | Persistence access mode                                                                     | `ReadWriteOnce`       |
| `persistence.media.enabled`            | Use persistent volume to store configuration data                                           | `true`                |
| `persistence.media.size`               | Size of persistent volume claim                                                             | `10Gi`                |
| `persistence.media.existingClaim`      | Use an existing PVC to persist data                                                         | `nil`                 |
| `persistence.media.storageClass`       | Type of persistent volume claim                                                             | `-`                   |
| `persistence.media.accessMode`         | Persistence access mode                                                                     | `ReadWriteOnce`       |
| `persistence.extraExistingClaimMounts` | Optionally add multiple existing claims                                                     | `[]`                  |
| `resources`                            | CPU/Memory resource requests/limits                                                         | `{}`                  |
| `nodeSelector`                         | Node labels for pod assignment                                                              | `{}`                  |
| `tolerations`                          | Toleration labels for pod assignment                                                        | `[]`                  |
| `affinity`                             | Affinity settings for pod assignment                                                        | `{}`                  |
| `env`                                  | Custom environment variables                                                                |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Read through the [values.yaml](values.yaml) file. It has several suggested values.
