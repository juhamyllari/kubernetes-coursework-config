# kubernetes-coursework-config

Deployment configuration for the project in [kubernetes-coursework](https://github.com/juhamyllari/kubernetes-coursework).
Argo CD deploys from this repository; the application source lives in the other one.

- `base/`: Kustomize manifests shared by all environments
- `overlays/staging`: namespace `staging`; image tags updated by the source repo's CI on every push to its `main`
- `overlays/production`: namespace `production`; image tags updated by the source repo's CI only when a `v*` tag is pushed
- `monitoring/`: Helm values for Prometheus, Grafana and Loki

The `images` block of each overlay's `kustomization.yaml` is written by CI. Secrets are not stored here.
