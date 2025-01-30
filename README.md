# ArgoCD Manifests Project

This repository contains Kubernetes manifests managed by ArgoCD, following the App of Apps pattern. The project is structured to support both development and production environments.

## Structure

- `apps/`: Contains the application manifests for each environment
  - `dev/`: Development environment application manifests
  - `prod/`: Production environment application manifests
- `bootstrap/`: Contains the App of Apps manifests
  - `dev/`: Development environment bootstrap manifests
  - `prod/`: Production environment bootstrap manifests

## Applications

1. Todo MVC App: `ghcr.io/docker-library/todomvc-app:latest`
2. Node Express App: `public.ecr.aws/docker/library/node-express:latest`
3. JSON Server: `clue/json-server:latest`
4. HTTP Echo Server: `hashicorp/http-echo:latest`

## Usage

1. First, apply the bootstrap application for the desired environment:
   ```bash
   kubectl apply -f bootstrap/dev/apps.yaml  # For development
   # or
   kubectl apply -f bootstrap/prod/apps.yaml # For production
   ```

2. ArgoCD will automatically sync and deploy all applications defined in the environment.

## Notes

- Each environment (dev/prod) has its own configuration
- The App of Apps pattern is used for better management and organization
- All applications are configured with appropriate resource limits and health checks 