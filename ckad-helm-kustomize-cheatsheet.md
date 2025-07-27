# CKAD 2025 - Helm & Kustomize Cheat Sheet

This cheat sheet summarizes the most useful **Helm** and **Kustomize** commands for the CKAD 2025 exam.

---

## 🛠️ Helm Commands

Helm is a Kubernetes package manager. Use it to install, upgrade, and manage applications via charts.

### ✅ Basics

```bash
# Add chart repository
helm repo add bitnami https://charts.bitnami.com/bitnami

# Update chart repos
helm repo update

# Search charts
helm search repo nginx

# Install a chart
helm install my-nginx bitnami/nginx
```

### ✅ Install Options

```bash
# Install to a specific namespace
helm install my-nginx bitnami/nginx --namespace dev --create-namespace

# Set values inline
helm install my-nginx bitnami/nginx --set replicaCount=2

# Use values from a file
helm install my-nginx bitnami/nginx -f values.yaml
```

### ✅ Chart Management

```bash
# List releases
helm list

# Upgrade release
helm upgrade my-nginx bitnami/nginx --set replicaCount=3

# Roll back release
helm rollback my-nginx 1

# Uninstall release
helm uninstall my-nginx
```

---

## 🧩 Kustomize Commands

Kustomize allows you to manage customized Kubernetes YAML configurations.

### ✅ Apply and Preview

```bash
# Apply a base or overlay
kubectl apply -k ./base

# Preview rendered YAML
kubectl kustomize ./base

# Dry-run apply
kubectl apply -k ./overlays/dev --dry-run=client -o yaml
```

### ✅ Common Fields in `kustomization.yaml`

```yaml
resources:
  - deployment.yaml
  - service.yaml

commonLabels:
  app: my-app

namePrefix: dev-

patchesStrategicMerge:
  - patch.yaml

configMapGenerator:
  - name: app-config
    literals:
      - MODE=production

secretGenerator:
  - name: app-secret
    literals:
      - TOKEN=abc123
```

---

### 💡 Tips:
- Helm is great for pre-packaged apps.
- Kustomize is ideal for managing environment-specific overlays.
- `kubectl apply -k` is your go-to for applying Kustomize configurations.
