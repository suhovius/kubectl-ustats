# ustats
DevOps Course Task. kubectl plugin that returns system resource usage status by resources

It is just a simple kubectl plugin implementation that has fixed formatting and might not work well with long values in the columns.

### Disclaimer

This is a test project. And normal plugin must be able installed via `krew` installer.

Read more here: [https://krew.sigs.k8s.io/docs/developer-guide/plugin-manifest/](https://krew.sigs.k8s.io/docs/developer-guide/plugin-manifest/)

### Installation

Clone git repository

`git clone git@github.com:suhovius/kubectl-ustats.git`

Make script executable

`chmod +x kubectl-ustats/scripts/ustats`

Create symlink to bin folder where kubectl expects this executable to be located:

`sudo ln -sf "$(pwd)/kubectl-ustats/scripts/ustats" /usr/local/bin/kubectl-ustats`

### Usage example

```
❯ kubectl ustats node kube-system
┌────────────────────────────────────────────────────┬──────────────────┬────────────┬────────────┐
│ Resource                                           │ Namespace        │ CPU        │ Memory     │
├────────────────────────────────────────────────────┼──────────────────┼────────────┼────────────┤
│ k3d-gitops-argocd-server-0                         │ kube-system      │ 186m       │ 2960Mi     │
└────────────────────────────────────────────────────┴──────────────────┴────────────┴────────────┘

❯ kubectl ustats pod kube-system 
┌────────────────────────────────────────────────────┬──────────────────┬────────────┬────────────┐
│ Resource                                           │ Namespace        │ CPU        │ Memory     │
├────────────────────────────────────────────────────┼──────────────────┼────────────┼────────────┤
│ coredns-6799fbcd5-pf6wv                            │ kube-system      │ 4m         │ 24Mi       │
│ local-path-provisioner-6f5d79df6-7hrl8             │ kube-system      │ 1m         │ 11Mi       │
│ metrics-server-54fd9b65b-vvnkx                     │ kube-system      │ 7m         │ 30Mi       │
│ svclb-traefik-0a8a8eb8-hnhw2                       │ kube-system      │ 0m         │ 0Mi        │
│ traefik-7d5f6474df-mnhpt                           │ kube-system      │ 1m         │ 38Mi       │
└────────────────────────────────────────────────────┴──────────────────┴────────────┴────────────┘
```