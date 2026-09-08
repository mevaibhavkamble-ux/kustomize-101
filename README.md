# kustomize-101

Sample app demonstrating Kustomize base/overlay pattern, deployed via ArgoCD.

## Structure

- `base/` — plain Kubernetes manifests, no environment-specific values
- `overlays/dev/` — dev environment: 2 replicas, nginx:1.25, namespace `dev`
- `overlays/prod/` — prod environment: 4 replicas, nginx:1.27, namespace `prod`

## Usage

Preview rendered manifests:

kubectl kustomize overlays/dev
kubectl kustomize overlays/prod


Apply directly:

kubectl apply -k overlays/dev

## GitOps

This repo is watched by ArgoCD (see `argocd-app.yaml` in this repo, or applied
separately to the cluster) — changes pushed to `main` are automatically synced.