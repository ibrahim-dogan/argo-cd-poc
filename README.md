# ArgoCD App of Apps Pattern

This repository demonstrates the App of Apps pattern for ArgoCD, which provides a hierarchical and scalable way to manage multiple applications.

## Repository Structure

```
.
├── apps/
│   ├── root-app/              # Root application that manages all other apps
│   │   └── root-application.yaml
│   ├── nginx/                 # Nginx application definition
│   │   └── nginx-application.yaml
│   └── flask-app/            # Flask application definition
│       └── flask-application.yaml
└── manifests/                # Actual application manifests
    ├── base/                 # Base configurations
    │   ├── nginx/
    │   └── flask-app/
    └── overlays/             # Environment-specific overlays
```

## Usage

1. Update the `repoURL` in all Application manifests to point to your repository.
2. Apply the root application to your ArgoCD instance:

```bash
kubectl apply -f apps/root-app/root-application.yaml
```

The root application will automatically create and manage the child applications (nginx and flask-app).

## Applications

- **Root Application**: Manages all other applications
- **Nginx**: Web server application
- **Flask App**: Python Flask application

Each application is configured with automated sync enabled, including pruning of resources and self-healing capabilities.