# helm-charts

This repository contains five demo Helm charts that deploy simple applications to Kubernetes.

## Available Charts

1. **nginx-demo** - Nginx web server (v1.25.0)
2. **apache-demo** - Apache HTTP Server (v2.4.58)
3. **busybox-demo** - BusyBox utility container (v1.36.1)
4. **redis-demo** - Redis cache server (v7.2.0)
5. **postgres-demo** - PostgreSQL database (v16.1)

## Usage

### Install from Source

```bash
# Clone the repository
git clone https://github.com/manno-test/helm-charts.git
cd helm-charts

# Install a chart
helm install my-nginx charts/nginx-demo
helm install my-apache charts/apache-demo
helm install my-busybox charts/busybox-demo
helm install my-redis charts/redis-demo
helm install my-postgres charts/postgres-demo
```

### Install from Helm Repository

Once the GitHub Pages is enabled, you can add this repository:

```bash
# Add the helm repository
helm repo add demo https://manno-test.github.io/helm-charts
helm repo update

# Install charts from the repository
helm install my-nginx demo/nginx-demo
helm install my-apache demo/apache-demo
helm install my-busybox demo/busybox-demo
helm install my-redis demo/redis-demo
helm install my-postgres demo/postgres-demo
```

## Development

### Linting Charts

```bash
helm lint charts/nginx-demo
helm lint charts/apache-demo
helm lint charts/busybox-demo
helm lint charts/redis-demo
helm lint charts/postgres-demo
```

### Packaging Charts

```bash
helm package charts/nginx-demo
helm package charts/apache-demo
helm package charts/busybox-demo
helm package charts/redis-demo
helm package charts/postgres-demo
```

## Automation

This repository uses GitHub Actions to automatically package and release charts:

- The workflow is triggered on changes to the `charts/` directory
- Charts are packaged and released to GitHub Pages
- The `index.yaml` file is automatically generated and updated

### Workflow

The release workflow (`.github/workflows/release-charts.yml`) uses the [chart-releaser-action](https://github.com/helm/chart-releaser-action) to:
1. Package the charts
2. Create GitHub releases
3. Generate and update the `index.yaml` file
4. Publish to GitHub Pages
