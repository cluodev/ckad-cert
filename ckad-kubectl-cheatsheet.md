# CKAD 2025 - `kubectl` Cheat Sheet

This printable cheat sheet lists the most essential `kubectl` commands categorized by the **latest CKAD 2025 exam domains**.

---

## ✅ 1. Application Design and Build

```bash
# Create a pod
kubectl run mypod --image=nginx

# Generate manifest (dry-run)
kubectl run mypod --image=nginx --dry-run=client -o yaml > pod.yaml

# Create a deployment
kubectl create deployment myapp --image=nginx

# Edit live resource
kubectl edit deployment myapp

# Explain resource structure
kubectl explain pod.spec.containers

# Validate YAML before applying
kubectl apply -f pod.yaml --dry-run=client

# Apply manifest
kubectl apply -f pod.yaml
```

---

## ✅ 2. Application Deployment

```bash
# Rolling update
kubectl set image deployment/myapp myapp=nginx:1.23

# Monitor rollout
kubectl rollout status deployment/myapp

# Rollback
kubectl rollout undo deployment/myapp

# Rollout history
kubectl rollout history deployment/myapp

# Apply Kustomize
kubectl apply -k ./overlays/staging

# Preview Kustomize output
kubectl kustomize ./overlays/staging
```

---

## ✅ 3. Application Observability and Maintenance

```bash
# Logs
kubectl logs mypod
kubectl logs mypod -c <container>
kubectl logs -p mypod

# Exec into container
kubectl exec -it mypod -- /bin/sh

# Describe resource
kubectl describe pod mypod

# View events
kubectl get events --sort-by='.metadata.creationTimestamp'

# view pod's ip addresses 
kubectl get pods -l app=foo -o wide

# View resource usage
kubectl top pod
kubectl top node

# Debug (if available)
kubectl debug pod/mypod --image=busybox
```

---

## ✅ 4. Application Env, Config, and Security

```bash
# Create ConfigMap and Secret
kubectl create configmap app-config --from-literal=ENV=prod
kubectl create secret generic app-secret --from-literal=key=supersecret

# View ConfigMaps and Secrets
kubectl get configmap
kubectl get secret
kubectl describe configmap app-config
kubectl describe secret app-secret

# Create ServiceAccount
kubectl create serviceaccount custom-sa

# View CRDs and custom resources
kubectl get crd
kubectl get <custom-resource>

# Resource limits reference
kubectl explain pod.spec.containers.resources
```

---

## ✅ 5. Services and Networking

```bash
# Expose a service
kubectl expose deployment myapp --port=80 --target-port=8080 --type=ClusterIP

# View services and endpoints
kubectl get svc
kubectl get endpoints

# Port forward
kubectl port-forward svc/myapp 8080:80

# Ingress
kubectl describe ingress my-ingress

# DNS lookup
kubectl exec mypod -- nslookup myapp

# Apply NetworkPolicy
kubectl apply -f policy.yaml

# Test service reachability
kubectl exec testpod -- curl http://myapp:80
# or create a temporary pod to run commands e.g. wget
kubectl run busybox --image=busybox --restart=Never -it --rm -- wget -O- <POD_IP>:8080

```

---

## 💡 General Tips

- Use `--dry-run=client -o yaml` to generate YAML without applying, available for `run` and `create` command groups
- Use `kubectl explain` to explore object schema
- Use `kubectl get all` for overview
- Add `-n <namespace>` when working in specific namespaces
- Use `kubectl config set-context [NAME | --current] [--namespace=namespace] [--cluster=clustername]` when working in specific context e.g. k config set-context minikube --namespace=ckad

### Resource shortnames

Run `kubectl api-resources` to get supported resource types and their shortnames

|name | shortnames |

|componentstatuses|	cs|

|configmaps | cm |

|endpoints |ep |

|events |ev |

namespaces ns

nodes no

persistentvolumeclaims pvc

persistentvolumes pv

pods po

serviceaccounts sa

services svc

customresourcedefinitions crd,crds

deployments deploy

replicasets rs

statefulsets sts

events ev

ingresses ing

networkpolicies netpol

storageclasses sc

helmcharts hc

helmreleases hr

### Useful Commands

#### Curl

```
curl -X GET https://graph.microsoft.com/v1.0/me \
  -H "Authorization: Bearer $TOKEN" \
  -H "Accept: application/json"
```

```
# debug response headers
curl -i -X GET https://api.example.com/resource
```

```
# only show status code
curl -s -o /dev/null -w "%{http_code}\n" https://api.example.com/health
```