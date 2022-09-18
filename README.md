# core-install
Core installation of a8n.

# Getting Started
Download [k3sup](https://github.com/alexellis/k3sup/releases) and follow their instructions to [setup a kubernetes server](https://github.com/alexellis/k3sup#-setup-a-kubernetes-server-with-k3sup).

`k3sup` creates a `kubeconfig` in the current directory with instructions to export the full path as `$KUBECONFIG`. Alternatively, the [k3s docs](https://rancher.com/docs/k3s/latest/en/cluster-access/#accessing-the-cluster-from-outside-with-kubectl) explain the config can be saved to `~/.kube/config` without requiring `$KUBECONFIG`.

```bash
export KUBECONFIG=`pwd`/kubeconfig
# OR
mkdir ~/.kube
cp kubeconfig ~/.kube/config
```

Follow the [docs](https://rancher.com/docs/k3s/latest/en/installation/kube-dashboard/) to install the kube dashboard.
