# Setup aliases 

Command aliases in terminal are very useful. 

```
#!/usr/local/bin/env bash

alias k='kubectl'
alias kg='kubectl get'
alias kgp='kubectl get pods'
alias kd='kubectl describe'
alias kt='kubectl top'
alias kf='kubectl config'
alias kaf='kubectl apply -f'
alias kcd='kubectl create deploy'
alias km='kustomize'

export dro='-dry-run=client -o yaml' # k create deploy nginx --image=nginx $dro
export k-now='-force --grace-period 0'
```

# K8s Documentation sites

- [quick reference](https://kubernetes.io/docs/reference/kubectl/quick-reference/)

- [Access apps in a cluster](https://kubernetes.io/docs/tasks/access-application-cluster/)

- [Tasks](https://kubernetes.io/docs/tasks/)