# Gitrepo Multidatacenter Example

This repo contains a simple example of how to use the Gitrepo module to deploy a multi-datacenter environment.

The datacenters folder contains the different datacenters argocd will manage. To deploy a new datacenter, create a new datacenter directory under the datacenters folder. Create a enviornment folder with in the datacenter an example `cluster-config.yaml` can be seen here. [cluster-config.yaml](datacenters/datacenter-1/dev/cluster-config.yaml). Under the cluster configs apps directory create a datacenter and environment and create a app `grafana-operator.yaml` is an example app that can be seen here. [grafana-operator.yaml](cluster-configs/apps/datacenter-1/dev/grafana-operator.yaml).