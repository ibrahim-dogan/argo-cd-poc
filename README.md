# Argo CD PoC

This repository demonstrates a proof of concept implementation of GitOps using Argo CD, showcasing continuous deployment for multiple applications with environment-specific configurations.

## Project Overview

This project includes:
- A Flask application deployment
- An Nginx deployment
- Multiple environment support (dev) using Kustomize
- Argo CD application configurations

## Prerequisites

- Kubernetes cluster
- Argo CD installed on the cluster
- kubectl CLI tool
- Git

## Repository Structure

```
.
├── flask-app/
│   ├── base/
│   │   ├── deployment.yaml
│   │   └── kustomization.yaml
│   └── overlays/
│       └── dev/
│           ├── application.yaml
│           ├── flask-patch.yaml
│           └── kustomization.yaml
├── nginx/
│   ├── base/
│   │   ├── deployment.yaml
│   │   └── kustomization.yaml
│   └── overlays/
│       └── dev/
│           ├── application.yaml
│           ├── nginx-patch.yaml
│           └── kustomization.yaml
└── root-application.yaml
```

## Applications

### Flask Application
The Flask application deployment is configured with:
- Base configuration in `flask-app/base/`
- Development environment specific configurations in `flask-app/overlays/dev/`

### Nginx Application
The Nginx deployment is configured with:
- Base configuration in `nginx/base/`
- Development environment specific configurations in `nginx/overlays/dev/`

## Kustomize Structure

Each application follows a Kustomize-based structure:
- `base/`: Contains the base Kubernetes manifests
- `overlays/`: Contains environment-specific modifications
  - `dev/`: Development environment configurations

## Argo CD Setup

1. Each application has its own Argo CD application configuration in the respective `overlays/dev/application.yaml`
2. The `root-application.yaml` serves as the main application that can be used to manage all child applications

## Usage

1. Install Argo CD in your Kubernetes cluster
2. Apply the root application:
   ```bash
   kubectl apply -f root-application.yaml
   ```
3. Argo CD will automatically sync and deploy both the Flask and Nginx applications according to their configurations

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details