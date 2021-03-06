# terraform-kubernetes-addons:aws

[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/terraform-kubernetes-addons)
[![terraform-kubernetes-addons](https://github.com/particuleio/terraform-kubernetes-addons/workflows/terraform-kubernetes-addons/badge.svg)](https://github.com/particuleio/terraform-kubernetes-addons/actions?query=workflow%3Aterraform-kubernetes-addons)

## About

Provides various Kubernetes addons that are often used on Kubernetes with AWS

## Main features

* Common addons with associated IAM permissions if needed:
  * [aws-ebs-csi-driver](https://github.com/kubernetes-sigs/aws-ebs-csi-driver): Enable new feature and the use of `gp3` volumes.
  * [aws-for-fluent-bit](https://github.com/aws/aws-for-fluent-bit): Cloudwatch logging with fluent bit instead of fluentd
  * [aws-load-balancer-controller](https://aws.amazon.com/about-aws/whats-new/2020/10/introducing-aws-load-balancer-controller/): Use AWS ALB/NLB for ingress and services.
  * [aws-node-termination-handler](https://github.com/aws/aws-node-termination-handler): Manage spot instance lifecyle
  * [aws-calico](https://github.com/aws/eks-charts/tree/master/stable/aws-calico): Use calico for network policy
  * [cert-manager](https://github.com/jetstack/cert-manager): automatically generate TLS certificates, supports ACME v2.
  * [cluster-autoscaler](https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler): scale worker nodes based on workload.
  * [cni-metrics-helper](https://docs.aws.amazon.com/eks/latest/userguide/cni-metrics-helper.html): Provides cloudwatch metrics for VPC CNI plugins.
  * [external-dns](https://github.com/kubernetes-incubator/external-dns): sync ingress and service records in route53.
  * [ingress-nginx](https://github.com/kubernetes/ingress-nginx): processes *Ingress* object and acts as a HTTP/HTTPS proxy (compatible with cert-manager).
  * [istio-operator](https://istio.io): Service mesh for Kubernetes.
  * [karma](https://github.com/prymitive/karma): An alertmanager dashboard
  * [keycloak](https://www.keycloak.org/) : Identity and access management
  * [kong](https://konghq.com/kong): API Gateway ingress controller.
  * [kube-prometheus-stack](https://github.com/prometheus-operator/kube-prometheus): Monitoring / Alerting / Dashboards.
  * [loki-stack](https://grafana.com/oss/loki/): Grafana Loki logging stack
  * [promtail](https://grafana.com/docs/loki/latest/clients/promtail/): Ship log to loki from other cluster (eg. mTLS)
  * [metrics-server](https://github.com/kubernetes-incubator/metrics-server): enable metrics API and horizontal pod scaling (HPA).
  * [node-problem-detector](https://github.com/kubernetes/node-problem-detector): Forwards node problems to Kubernetes events
  * [sealed-secrets](https://github.com/bitnami-labs/sealed-secrets): Technology agnostic, store secrets on git.
  * [thanos](https://thanos.io/): Open source, highly available Prometheus setup with long term storage capabilities
  * [thanos-storegateway](https://thanos.io/): Additional storegateway to query multiple object stores
  * [thanos-tls-querier](https://thanos.io/tip/operating/cross-cluster-tls-communication.md/): Thanos TLS querier for cross cluster collection

## Documentation

User guides, feature documentation and examples are available [here](https://particuleio.github.io/teks/)

## IAM permissions

This module can uses [IRSA](https://aws.amazon.com/blogs/opensource/introducing-fine-grained-iam-roles-service-accounts/).

## Terraform docs

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.13 |
| aws | ~> 3.0 |
| helm | ~> 2.0 |
| kubectl | ~> 1.0 |
| kubernetes | ~> 1.0 |

## Providers

| Name | Version |
|------|---------|
| aws | ~> 3.0 |
| helm | ~> 2.0 |
| kubectl | ~> 1.0 |
| kubernetes | ~> 1.0 |
| random | n/a |
| time | n/a |
| tls | n/a |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| aws | AWS provider customization | `any` | `{}` | no |
| aws-ebs-csi-driver | Customize aws-ebs-csi-driver helm chart, see `aws-ebs-csi-driver.tf` | `any` | `{}` | no |
| aws-for-fluent-bit | Customize aws-for-fluent-bit helm chart, see `aws-fluent-bit.tf` | `any` | `{}` | no |
| aws-load-balancer-controller | Customize aws-load-balancer-controller chart, see `aws-load-balancer-controller.tf` for supported values | `any` | `{}` | no |
| aws-node-termination-handler | Customize aws-node-termination-handler chart, see `aws-node-termination-handler.tf` | `any` | `{}` | no |
| calico | Customize calico helm chart, see `calico.tf` | `any` | `{}` | no |
| cert-manager | Customize cert-manager chart, see `cert-manager.tf` for supported values | `any` | `{}` | no |
| cluster-autoscaler | Customize cluster-autoscaler chart, see `cluster-autoscaler.tf` for supported values | `any` | `{}` | no |
| cluster-name | Name of the Kubernetes cluster | `string` | `"sample-cluster"` | no |
| cni-metrics-helper | Customize cni-metrics-helper deployment, see `cni-metrics-helper.tf` for supported values | `any` | `{}` | no |
| eks | EKS cluster inputs | `any` | `{}` | no |
| external-dns | Map of map for external-dns configuration: see `external_dns.tf` for supported values | `any` | `{}` | no |
| flux | Customize Flux chart, see `flux.tf` for supported values | `any` | `{}` | no |
| helm\_defaults | Customize default Helm behavior | `any` | `{}` | no |
| ingress-nginx | Customize ingress-nginx chart, see `nginx-ingress.tf` for supported values | `any` | `{}` | no |
| istio-operator | Customize istio operator deployment, see `istio_operator.tf` for supported values | `any` | `{}` | no |
| karma | Customize karma chart, see `karma.tf` for supported values | `any` | `{}` | no |
| keycloak | Customize keycloak chart, see `keycloak.tf` for supported values | `any` | `{}` | no |
| kong | Customize kong-ingress chart, see `kong.tf` for supported values | `any` | `{}` | no |
| kube-prometheus-stack | Customize kube-prometheus-stack chart, see `kube-prometheus-stack.tf` for supported values | `any` | `{}` | no |
| labels\_prefix | Custom label prefix used for network policy namespace matching | `string` | `"particule.io"` | no |
| loki-stack | Customize loki-stack chart, see `loki-stack.tf` for supported values | `any` | `{}` | no |
| metrics-server | Customize metrics-server chart, see `metrics_server.tf` for supported values | `any` | `{}` | no |
| npd | Customize node-problem-detector chart, see `npd.tf` for supported values | `any` | `{}` | no |
| priority-class | Customize a priority class for addons | `any` | `{}` | no |
| priority-class-ds | Customize a priority class for addons daemonsets | `any` | `{}` | no |
| promtail | Customize promtail chart, see `loki-stack.tf` for supported values | `any` | `{}` | no |
| sealed-secrets | Customize sealed-secrets chart, see `sealed-secrets.tf` for supported values | `any` | `{}` | no |
| tags | Map of tags for AWS resources | `map(any)` | `{}` | no |
| thanos | Customize thanos chart, see `thanos.tf` for supported values | `any` | `{}` | no |
| thanos-storegateway | Customize thanos chart, see `thanos.tf` for supported values | `any` | `{}` | no |
| thanos-tls-querier | Customize thanos chart, see `thanos.tf` for supported values | `any` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| grafana\_password | n/a |
| loki-stack-ca | n/a |
| promtail-cert | n/a |
| promtail-key | n/a |
| thanos\_ca | n/a |

