# Multi-Datacenter Environment Deployment using ArgoCD

This repository contains a simple example of how to use the Gitrepo module to deploy a multi-datacenter environment using ArgoCD. It is structured in a way to manage different datacenters and their respective environments and applications.

## Repository Structure

The repository is organized as follows:

```
├── README.md
├── cluster-configs
│   └── apps
│       ├── datacenter-1
│       │   ├── dev
│       │   │   └── grafana-operator.yaml
│       │   ├── prod
│       │   │   ├── external-secrets-operator.yaml
│       │   │   └── grafana-operator.yaml
│       │   └── qa
│       │       └── grafana-operator.yaml
│       └── datacenter-2
│           ├── dev
│           │   └── grafana-operator.yaml
│           ├── prod
│           │   ├── external-secrets-operator.yaml
│           │   └── grafana-operator.yaml
│           └── qa
│               └── grafana-operator.yaml
├── datacenters
│   ├── datacenter-1
│   │   ├── dev
│   │   │   └── cluster-config.yaml
│   │   ├── prod
│   │   │   └── cluster-config.yaml
│   │   └── qa
│   │       └── cluster-config.yaml
│   └── datacenter-2
│       ├── dev
│       │   └── cluster-config.yaml
│       ├── prod
│       │   └── cluster-config.yaml
│       └── qa
│           └── cluster-config.yaml
├── external-secrets-operator
│   ├── README.md
│   ├── instance
│   │   ├── base
│   │   │   ├── default-operatorconfig.yaml
│   │   │   ├── kustomization.yaml
│   │   │   └── namespace.yaml
│   │   └── overlays
│   │       └── default
│   │           └── kustomization.yaml
│   └── operator
│       ├── base
│       │   ├── kustomization.yaml
│       │   └── subscription.yaml
│       └── overlays
│           ├── README.md
│           ├── alpha
│           │   └── kustomization.yaml
│           └── stable
│               └── kustomization.yaml
└── grafana-operator
    ├── README.md
    ├── base
    │   ├── instance
    │   │   ├── grafana-proxy-rbac.yaml
    │   │   ├── grafana.yaml
    │   │   ├── kustomization.yaml
    │   │   └── session-secret.yaml
    │   └── operator
    │       ├── kustomization.yaml
    │       └── subscription.yaml
    └── overlays
        ├── aggregate
        │   └── kustomization.yaml
        ├── example
        │   ├── kustomization.yaml
        │   ├── namespace.yaml
        │   └── operator-group.yaml
        ├── user-app
        │   ├── README.md
        │   ├── cluster-monitor-view-rb.yaml
        │   ├── grafana-auth-secret.yaml
        │   ├── grafana-ds.yaml
        │   └── kustomization.yaml
        └── user-app-example
            ├── README.md
            ├── kustomization.yaml
            ├── namespace.yaml
            ├── operator-group.yaml
            ├── patch-cluster-monitoring-view.yaml
            └── patch-grafana-sar.yaml

38 directories, 47 files
```

## How to Deploy a New Datacenter

To deploy a new datacenter, follow these steps:

1. Create a new directory under the `datacenters` folder for the new datacenter.
2. Within the new datacenter directory, create environment folders (e.g., `dev`, `prod`, `qa`) as needed.
3. In each environment folder, create a `cluster-config.yaml` file. This file should contain the configuration specific to that datacenter and environment. You can use [cluster-config.yaml](datacenters/datacenter-1/dev/cluster-config.yaml) as an example.
4. Under the `cluster-configs/apps` directory, create a new directory for the new datacenter (e.g., `datacenter-3`).
5. Within the new datacenter directory, create environment folders (e.g., `dev`, `prod`, `qa`) similar to the ones created in the `datacenters` folder.
6. In each environment folder, create an application YAML file (e.g., `grafana-operator.yaml`) for the applications you want to deploy in that specific datacenter and environment. You can use [grafana-operator.yaml](cluster-configs/apps/datacenter-1/dev/grafana-operator.yaml) as an example.
7. If you need to add new applications, create a new application using [kustomize](https://kustomize.io/) under the root directory of the repository. Once the application is created, add it to the respective datacenter's `cluster-configs` directory. Using [grafana-operator.yaml](cluster-configs/apps/datacenter-1/dev/grafana-operator.yaml) as an example.

## Managing External Secrets Operator and Grafana Operator

The repository includes two operators, `external-secrets-operator` and `grafana-operator`, that are managed for each datacenter and environment. They are organized under their respective directories. Refer to the `README.md` files inside each operator directory for specific instructions on how to use and configure them.

## Conclusion

This README provides a basic understanding of the repository structure and how to deploy new datacenters and manage applications using ArgoCD. Feel free to explore the specific directories and files for more details and configurations of each component. If you have any questions or need further assistance, please refer to the relevant `README.md` files or reach out to the repository maintainers. Happy deploying!