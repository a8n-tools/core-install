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

```bash
k3sup install --local --local-path ~/.kube/config --k3s-channel=latest --k3s-extra-args "--advertise-address=172.30.0.21"

kubectl get node -o wide

GITHUB_URL=https://github.com/kubernetes/dashboard/releases
VERSION_KUBE_DASHBOARD=$(curl -w '%{url_effective}' -I -L -s -S ${GITHUB_URL}/latest -o /dev/null | sed -e 's|.*/||')
k3s kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/${VERSION_KUBE_DASHBOARD}/aio/deploy/recommended.yaml
k3s kubectl create -f dashboard.admin-user.yml -f dashboard.admin-user-role.yml
k3s kubectl -n kubernetes-dashboard create token admin-user

k3s kubectl proxy
```

<http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/>

<https://kubernetes.io/docs/concepts/workloads/controllers/deployment/>

<https://www.atomiccommits.io/everything-useful-i-know-about-kubectl>

<https://www.amazon.com/Myth-Most-Businesses-Dont-About/dp/0887303625>

<https://www.amazon.com/Myth-Revisited-Small-Businesses-About/dp/0887307280>

<https://github.com/amidaware/trmm-awesome/tree/main/kubernetes>

<https://github.com/kubernetes/dashboard#install>

<https://rancher.com/docs/k3s/latest/en/installation/kube-dashboard/>


