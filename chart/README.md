# sulfoxide-tin

![Version: 1.9.0](https://img.shields.io/badge/Version-1.9.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.13.1](https://img.shields.io/badge/AppVersion-1.13.1-informational?style=flat-square)

Helm chart to deploy External DNS to configure DNS records to DNS providers

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://kubernetes-sigs.github.io/external-dns/ | external-dns | 1.14.5 |
| oci://ghcr.io/atomicloud/sulfoxide.bromine | sulfoxide-bromine | 1.6.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| external-dns | object | `{"commonLabels":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/module":"controller","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"tin"}},"deploymentAnnotations":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/module":"controller","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"tin"}},"env":[{"name":"CF_API_TOKEN","valueFrom":{"secretKeyRef":{"key":"CLOUDFLARE_TOKEN","name":"cloudflare-external-dns-token"}}}],"interval":"1m","logFormat":"json","podAnnotations":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/module":"controller","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"tin"}},"podLabels":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/module":"controller","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"tin"}},"podSecurityContext":{"<<":{"fsGroup":1000,"runAsGroup":1000,"runAsNonRoot":true,"runAsUser":1000}},"policy":"upsert-only","provider":"cloudflare","rbac":{"create":true},"resources":{"limits":{"cpu":1,"memory":"1Gi"},"requests":{"cpu":"250m","memory":"256Mi"}},"securityContext":{"<<":{"allowPrivilegeEscalation":false,"capabilities":{"drop":["ALL"]},"readOnlyRootFilesystem":true,"runAsGroup":3000,"runAsNonRoot":true,"runAsUser":1000}},"serviceMonitor":{"enabled":true},"sources":["service"],"topologySpreadConstraints":[{"labelSelector":{"matchLabels":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/module":"controller","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"tin"}}},"maxSkew":1,"topologyKey":"topology.kubernetes.io/zone","whenUnsatisfiable":"ScheduleAnyway"}]}` | ExternalDNS configuration. See [ExternalDNS Helm Chart](https://github.com/kubernetes-sigs/external-dns/tree/master/charts/external-dns) |
| podSecurityContext | object | `{"fsGroup":1000,"runAsGroup":1000,"runAsNonRoot":true,"runAsUser":1000}` | YAML Anchor for PodSecurityContext |
| secretAnnotation | object | `{"argocd.argoproj.io/sync-wave":"-2"}` | Secret Annotations (External Secrets) to control synchronization |
| securityContext | object | `{"allowPrivilegeEscalation":false,"capabilities":{"drop":["ALL"]},"readOnlyRootFilesystem":true,"runAsGroup":3000,"runAsNonRoot":true,"runAsUser":1000}` | YAML Anchor for SecurityContext |
| serviceTree | object | `{"layer":"1","module":"controller","platform":"sulfoxide","service":"tin"}` | AtomiCloud Service Tree. See [ServiceTree](https://atomicloud.larksuite.com/wiki/OkfJwTXGFiMJkrk6W3RuwRrZs64?theme=DARK&contentTheme=DARK#MHw5d76uDo2tBLx86cduFQMRsBb) |
| sulfoxide-bromine | object | `{"annotations":{"argocd.argoproj.io/sync-wave":"-3"},"rootSecret":{"name":"tin","ref":{"clientId":"SULFOXIDE_TIN_CLIENT_ID","clientSecret":"SULFOXIDE_TIN_CLIENT_SECRET"}},"serviceTree":{"platform":"sulfoxide","service":"tin"},"storeName":"tin"}` | Create SecretStore via secret of secrets pattern |
| sulfoxide-bromine.rootSecret | object | `{"name":"tin","ref":{"clientId":"SULFOXIDE_TIN_CLIENT_ID","clientSecret":"SULFOXIDE_TIN_CLIENT_SECRET"}}` | Secret of Secrets reference |
| sulfoxide-bromine.storeName | string | `"tin"` | Store name to create |
| tags | object | `{"atomi.cloud/layer":"1","atomi.cloud/module":"controller","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"tin"}` | Kubernetes labels and annotations, following Service Tree |
| token | object | `{"external":{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"CLOUDFLARE_EXTERNAL_DNS_TOKEN","secretStore":{"kind":"SecretStore","name":"tin"}},"internal":{"enable":false,"token":""},"secretName":"cloudflare-external-dns-token"}` | Cloudflare Tunnel Token |
| token.external | object | `{"enable":true,"policy":{"creation":"Owner","deletion":"Retain"},"refreshInterval":"1h","remoteSecretName":"CLOUDFLARE_EXTERNAL_DNS_TOKEN","secretStore":{"kind":"SecretStore","name":"tin"}}` | Use external secret |
| token.external.enable | bool | `true` | Enable the use of external secret |
| token.external.policy | object | `{"creation":"Owner","deletion":"Retain"}` | Secret policy |
| token.external.policy.creation | string | `"Owner"` | Creation policy |
| token.external.policy.deletion | string | `"Retain"` | Deletion policy |
| token.external.refreshInterval | string | `"1h"` | Refresh Rate |
| token.external.remoteSecretName | string | `"CLOUDFLARE_EXTERNAL_DNS_TOKEN"` | Remote Secret Reference name |
| token.external.secretStore.kind | string | `"SecretStore"` | Kind of the Secret Store: `ClusterSecretStore` or `SecretStore` |
| token.external.secretStore.name | string | `"tin"` | Name of the Secret Store |
| token.internal | object | `{"enable":false,"token":""}` | Secret directly inlined in value files |
| token.internal.enable | bool | `false` | Use hard coded secret |
| token.internal.token | string | `""` | Hard coded Cloudflare token |
| token.secretName | string | `"cloudflare-external-dns-token"` | Secret Name that stores the Token with key CLOUDFLARE_TOKEN |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
