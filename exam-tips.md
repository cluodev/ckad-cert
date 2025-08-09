# Setup aliases 

Command aliases in terminal are very useful. 

<details>
<summary>show</summary>
<p>

```
#!/usr/local/bin/env bash

alias k='kubectl'
alias kg='kubectl get'
alias kgp='kubectl get pods'
alias kd='kubectl describe'
alias kt='kubectl top'
alias kf='kubectl config'
alias kaf='kubectl apply -f'
alias kak='kubectl apply -k' # applying kustomize configurations e.g. kak ./base
alias kcd='kubectl create deploy'
alias km='kustomize'
alias kk='kubectl kustomize'
alias kbbox='k run busybox --image=busybox --restart=Never -it --rm' # run a temp pod busybox

export dro='--dry-run=client -o yaml' # k create deploy nginx --image=nginx $dro
export k-now='-force --grace-period 0'
```

</p>
</details>

# K8s Documentation sites

- [quick reference](https://kubernetes.io/docs/reference/kubectl/quick-reference/)

- [Access apps in a cluster](https://kubernetes.io/docs/tasks/access-application-cluster/)

- [Tasks](https://kubernetes.io/docs/tasks/)

  [CRDs](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#field-selectors)

  [Kustomize](https://kubernetes.io/docs/tasks/manage-kubernetes-objects/kustomization/)

- [Concepts](https://kubernetes.io/docs/concepts/)

e.g. Containers, Workloads (pods, ), Services, Load balancing, Networking, etc

- [K8s API](https://kubernetes.io/docs/reference/kubernetes-api/)

- [kubectl commands](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)

- [kubectl reference](https://kubernetes.io/docs/reference/kubectl/generated/)

- [Helm Docs](https://helm.sh/docs/)


# Other useful resources

CKAD exercises: https://github.com/dgkanatsios/CKAD-exercises

Important instructions: CKA and CKAD: https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad

Official CKAD Introduction page: https://www.cncf.io/training/certification/ckad/

Using Google NotebookLM



