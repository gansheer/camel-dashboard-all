<h1 align="center">
  <a href="https://camel-tooling.github.io/camel-dashboard/">Camel Dashboard Openshift Helm Chart</a>
</h1>

<p align=center>
  <a href="https://github.com/camel-tooling/camel-dashboard/blob/main/LICENSE"><img src="https://img.shields.io/github/license/camel-tooling/camel-monitor-operator?color=104d92&style=for-the-badge" alt="License"/></a>
  <a href="https://camel-tooling.github.io/camel-dashboard/"><img src="https://img.shields.io/badge/Documentation-Camel_Dashboard-white?color=cf7428&style=for-the-badge" alt="Visit"/></a>
</p><br/>

<h2 align="center">Camel Dashboard All-in-One Helm Chart for Openshift</h2>


This is an umbrella Helm chart that deploys the complete Camel Dashboard solution, including:
- **Camel Monitor Operator**: Manages Camel Monitor instances
- **Camel Dashboard Console**: OpenShift Console plugin for Camel Dashboard
- **Hawtio Online Console Plugin**: Management and monitoring console for Java applications

## Prerequisites

- Kubernetes
- Helm
- OpenShift 4.19+

## Installation

### 1. Add the Helm Repository

```bash
helm repo add camel-dashboard https://camel-tooling.github.io/camel-dashboard/charts
helm repo update
```

### 2. Install the Chart

```bash
helm install camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard --create-namespace
```


### 3. Customizing Installation

You can customize the installation by providing your own values:

```bash
helm install camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard --create-namespace -f my-values.yaml
```

## Upgrading

### Upgrading from 4.21.1 or earlier to 4.21.2

**Important**: Helm does not automatically upgrade CRDs during chart upgrades. Version 4.21.2 introduces new CRDs from `camel-monitor-operator` v0.2.1. You must manually apply these CRDs before running `helm upgrade`:

```bash
# Update your Helm repository
helm repo update

# Apply the new CRDs manually (from camel-monitor-operator v0.2.1)
kubectl apply -f https://raw.githubusercontent.com/camel-tooling/camel-monitor-operator/v0.2.1/helm/camel-monitor/crds/camel-monitor-crds.yaml

# Now upgrade the chart
helm upgrade camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard
```

### General Upgrade Procedure

For regular upgrades (when no new CRDs are introduced):

```bash
helm repo update
helm upgrade camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard
```

## Uninstalling

```bash
helm uninstall camel-dashboard-openshift-all -n camel-dashboard
```


## More Information

- [Camel Dashboard Documentation](https://camel-tooling.github.io/camel-dashboard/)
- [Camel Dashboard Repository](https://github.com/camel-tooling/camel-dashboard)
- [Camel Monitor Operator](https://github.com/camel-tooling/camel-monitor-operator)
- [Camel Dashboard Console](https://github.com/camel-tooling/camel-dashboard-console)
- [Hawtio Console Plugin](https://github.com/hawtio/hawtio-online)
- [Apache Camel](https://camel.apache.org/)
