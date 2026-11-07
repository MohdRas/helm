The Kubernetes package manager

Helm Hub ( Artifacthub.io ) -  contains repositories( appscode, truecharts, bitnami, communityoperators) - contains charts.
when a chart is applied to kubernetes , a release created - creating multiple releases based on chart.

From Helm's perspective:
Chart: A package or template that defines Kubernetes resources (like deployments, services, etc.). Think of it as a blueprint or recipe.
Release: An instance of a chart deployed into Kubernetes. It’s a specific deployment of that chart with its own configuration and version history.
From Kubernetes objects' perspective:
Chart: The set of resource definitions (YAML templates) stored in Helm; it’s not directly a Kubernetes object.
Release: The actual Kubernetes objects (pods, services, deployments, etc.) created and managed by Helm when you install or upgrade a chart.
Where they sit:
Chart: Stored locally or in repositories; it’s the template package.
Release: The live, running set of Kubernetes objects created from the chart, with Helm tracking its state and history.
In short:

Chart = blueprint/template
Release = deployed, live instance of that blueprint in Kubernetes


For Releases (managing deployed apps):
helm install release-name chart-name: Deploys a new chart as a release into Kubernetes, creating resources.
helm list: Lists all current Helm releases in the specified namespace.
helm upgrade: Upgrades an existing release to a new chart version or configuration.
helm uninstall: Removes a release and all its associated resources from Kubernetes.
helm rollback: Reverts a release to a previous version, undoing recent changes.

For Charts (working with templates/packages):
helm search: Searches Helm repositories for charts matching a keyword.
helm repo add: Adds a new chart repository to your Helm configuration.
helm repo update: Refreshes the local cache of chart repositories.
helm create: Creates a new, empty chart scaffold with default files.
helm package: Packages a chart directory into a versioned archive (.tgz file).


A standard format to type Helm commands is:

helm <command> [options] [arguments]

For example:

For releases: helm install my-release my-chart
<command>: install
[options]: none (no options used here)
[arguments]: my-release, my-chart

For charts: helm search repo nginx
<command>: search
[subcommand]: repo ( search repo is a command sequence)
[arguments]: nginx

helm install my-release my-chart --namespace my-namespace
<command>: install
[options]: --namespace my-namespace
[arguments]: my-release, my-chart


environment settings
controlplane ~ ➜  helm env
HELM_BIN="helm"
HELM_BURST_LIMIT="100"
HELM_CACHE_HOME="/root/.cache/helm"
HELM_CONFIG_HOME="/root/.config/helm"
HELM_CONTENT_CACHE="/root/.cache/helm/content"
HELM_DATA_HOME="/root/.local/share/helm"
HELM_DEBUG="false"
HELM_KUBEAPISERVER=""
HELM_KUBEASGROUPS=""
HELM_KUBEASUSER=""
HELM_KUBECAFILE=""
HELM_KUBECONTEXT=""
HELM_KUBEINSECURE_SKIP_TLS_VERIFY="false"
HELM_KUBETLS_SERVER_NAME=""
HELM_KUBETOKEN=""
HELM_MAX_HISTORY="10"
HELM_NAMESPACE="default"
HELM_PLUGINS="/root/.local/share/helm/plugins"
HELM_QPS="0.00"
HELM_REGISTRY_CONFIG="/root/.config/helm/registry/config.json"
HELM_REPOSITORY_CACHE="/root/.cache/helm/repository"
HELM_REPOSITORY_CONFIG="/root/.config/helm/repositories.yaml"

HELM_BIN: Path to the Helm executable, here just "helm".
HELM_BURST_LIMIT: Max number of concurrent requests Helm can make, set to 100.
HELM_CACHE_HOME: Directory for Helm's cache files, here /root/.cache/helm.
HELM_CONFIG_HOME: Directory for Helm's configuration files, /root/.config/helm.
HELM_CONTENT_CACHE: Cache for chart content, located in /root/.cache/helm/content.
HELM_DATA_HOME: Data directory for Helm, /root/.local/share/helm.
HELM_DEBUG: Debug mode toggle; "false" means debugging is off.
HELM_KUBEAPISERVER: URL of the Kubernetes API server (empty here, defaults used).
HELM_KUBEASGROUPS: Groups for impersonation, empty here.
HELM_KUBEASUSER: User for impersonation, empty here.
HELM_KUBECAFILE: Path to CA certificate file for TLS, empty here.
HELM_KUBECONTEXT: Kubernetes context name, empty here (defaults used).
HELM_KUBEINSECURE_SKIP_TLS_VERIFY: Skip TLS verification for API server; "false" means strict verification.
HELM_KUBETLS_SERVER_NAME: Server name for TLS verification, empty here.
HELM_KUBETOKEN: Bearer token for authentication, empty here.
HELM_MAX_HISTORY: Max number of release revisions stored; set to 10.
HELM_NAMESPACE: Kubernetes namespace Helm operates in; default is "default".
HELM_PLUGINS: Directory for Helm plugins, /root/.local/share/helm/plugins.
HELM_QPS: Queries per second limit for API requests; "0.00" means no limit.
HELM_REGISTRY_CONFIG: Path to registry configuration JSON, /root/.config/helm/registry/config.json.
HELM_REPOSITORY_CACHE: Cache for chart repositories, /root/.cache/helm/repository.
HELM_REPOSITORY_CONFIG: Repositories configuration file, /root/.config/helm/repositories.yaml.
