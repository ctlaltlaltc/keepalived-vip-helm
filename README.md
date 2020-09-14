# kube-keepalived-vip

The [kube-keepalived-vip](https://github.com/ctlaltlaltc/keepalived-vip) Highly available IP addresses and services.

## TL;DR;

```console
$ helm install --name my-release --set keepalived.config.'192\.168\.20\.253'="" --set keepalived.vrid=179 stable/kube-keepalived-vip
```

## Prerequisites

- Kubernetes 1.6+
- Virtual ip address(VIP)

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release --set keepalived.config.'192\.168\.20\.253'="" --set keepalived.vrid=179 stable/kube-keepalived-vip
$ # helm install --name my-release --set keepalived.config.'192\.168\.20\.252'=my-namespace/mysvc --set keepalived.vrid=179 stable/kube-keepalived-vip
```

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of this chart and their default values.

| Parameter                         | Description                                 | Default                                                   |
| --------------------------------- | -------------------------------------       | --------------------------------------------------------- |
| `keepalived.name`                    | keepalived container name | `keepalived`                                                         |
| `keepalived.image.repository`                    | Docker image repo | `ghcr.io/ctlaltlaltc/keepalived-vip/kube-keepalived-vip`                                                         |
| `keepalived.image.tag`                    | Docker image tag | `latest`                                                         |
| `keepalived.image.pullPolicy`                    | Docker image pullPolicy| `IfNotPresent`                                                         |
| `keepalived.config`                    | keepalived vip-configmap | `{}`                                                         |
| `keepalived.vips`                    | keepalived only virtual ips do not contain service | `[]`                                                         |
| `keepalived.useUnicast`                    | keepalived use  Unicast, use Unicast maybe [issue](https://github.com/acassen/keepalived/issues/642) about checksum| `false`                                                         |
| `keepalived.vrid`                    | keepalived vrid | `179`                                                         |
| `keepalived.resources`                    | keepalived daemonset resource | `{}`                                                         |
| `keepalived.watchAllNamespace`                    | keepalived watchAllNamespace | `true`                                                         |
| `fullnameOverride`                    | fullnameOverride | `null`                                  |
| `nameOverride`                | nameOverride                           | `null`         |
| `revisionHistoryLimit`                       | daemonset revisionHistoryLimit                | `10`                                          |
| `updateStrategy`                | updateStrategy                           | `{}`                                            |
| `podLabels`                       | podLabels       | `{}`                                                      |
| `tolerations`                       | tolerations       | `[]`                                                      |
| `nodeSelector`                       | nodeSelector       | `[]`                                                      |
| `podAnnotations`                       | podAnnotations       | `{}`                                                      |
| `affinity.enabled`                       | daemonset affinity enabled or not       | `false`                                                      |
| `affinity.nodes`                       | daemonset affinity nodes by array hostname       | `[]`                                                      |
| `rbac.create`                       | rbac.create       | `true`                                                      |
| `rbac.serviceAccountName`                       | rbac.serviceAccountName       | `default`                                                      |
