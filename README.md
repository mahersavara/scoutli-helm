# Scoutli Helm Charts

This repository serves as the central storage for the [Helm](https://helm.sh/) charts used to deploy the Scoutli application to Kubernetes.

## Chart Structure

```
charts/
└── scoutli/            # The main Umbrella Chart
    ├── Chart.yaml      # Chart metadata
    ├── values.yaml     # Default configuration values
    ├── templates/      # Kubernetes manifest templates
    │   ├── deployment-backend.yaml
    │   ├── deployment-frontend.yaml
    │   ├── service-backend.yaml
    │   ├── service-frontend.yaml
    │   ├── ingress.yaml
    │   └── ...
    └── charts/         # Sub-charts (if any)
```

## Usage

This chart is designed to be consumed by **ArgoCD** for GitOps deployment. However, you can also install it manually:

1.  Update `values.yaml` with your specific configuration (e.g., image tags, domain name).
2.  Install/Upgrade:
    ```bash
    helm upgrade --install scoutli ./charts/scoutli -n scoutli-app --create-namespace
    ```

## Configuration

Key configuration parameters in `values.yaml`:

| Key | Description | Default |
| --- | --- | --- |
| `backend.image.repository` | Backend Docker image repo | `.../scoutli-backend` |
| `backend.image.tag` | Backend image tag | `latest` |
| `frontend.image.repository` | Frontend Docker image repo | `.../scoutli-frontend` |
| `frontend.image.tag` | Frontend image tag | `latest` |
| `ingress.enabled` | Enable Ingress creation | `true` |