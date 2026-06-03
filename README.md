# Camel Dashboard OpenShift All

Camel Dashboard All-in-One Helm Chart for Openshift

This is an umbrella Helm chart that deploys the complete Camel Dashboard solution, including:
- **Camel Monitor Operator**: Manages Camel Monitor instances
- **Camel Dashboard Console**: OpenShift Console plugin for Camel Dashboard
- **Hawtio Online Console Plugin**: Management and monitoring console for Java applications

## Version Compatibility

This Helm chart follows a versioning scheme aligned with OpenShift versions:
- **Chart version X.Y.Z** is compatible with **OpenShift X.Y**
- The patch version (Z) indicates chart-specific updates that don't change OCP compatibility

**Note**: Always use the latest patch version of the chart for your OpenShift version.

## Prerequisites

- OpenShift 4.21

## Installation procedure

Add repository
```
helm repo add camel-dashboard https://camel-tooling.github.io/camel-dashboard/charts
```

Install chart
```
$ helm install camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard --create-namespace
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

### 3. Customizing Installation

You can customize the installation by providing your own values:

```bash
helm install camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard --create-namespace -f my-values.yaml
```

For more installation configuration on the Camel Dashboard please see the [installation documentation](https://camel-tooling.github.io/camel-dashboard/docs/installation-guide/).


## More Information

- [Camel Dashboard Documentation](https://camel-tooling.github.io/camel-dashboard/)
- [Camel Dashboard Repository](https://github.com/camel-tooling/camel-dashboard)
- [Camel Monitor Operator](https://github.com/camel-tooling/camel-monitor-operator)
- [Camel Dashboard Console](https://github.com/camel-tooling/camel-dashboard-console)
- [Hawtio Console Plugin](https://github.com/hawtio/hawtio-online)
- [Apache Camel](https://camel.apache.org/)