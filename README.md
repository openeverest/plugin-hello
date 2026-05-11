# OpenEverest Hello Plugin

A sample plugin for [OpenEverest](https://github.com/openeverest/openeverest) that demonstrates the generic plugin architecture.

## Prerequisites

- An OpenEverest cluster with the Plugin CRD installed (comes with Everest v2+)

## Install with Helm

```bash
helm install hello charts/plugin-hello/ -n everest-system
```

## Uninstall

```bash
helm uninstall hello -n everest-system
```

## Local Development

### Build the plugin bundle

```bash
npm install
npm run build    # produces dist/main.js
```

### Dev server (standalone)

```bash
npm run dev      # serves on http://localhost:3001
```

### Build Docker image

```bash
npm run build
docker build -t plugin-hello:dev .
```

### Tilt (with OpenEverest dev environment)

Set `HELLO_PLUGIN_DIR` to point to this repo's root in your Tilt environment:

```bash
export HELLO_PLUGIN_DIR=/path/to/plugin-hello
cd /path/to/openeverest/dev
tilt up
```

## Configuration (values.yaml)

| Parameter | Description | Default |
|-----------|-------------|---------|
| `image.repository` | Plugin container image | `ghcr.io/openeverest/plugin-hello` |
| `image.tag` | Image tag (defaults to chart appVersion) | `""` |
| `replicaCount` | Number of replicas | `1` |
| `service.port` | Service port | `3001` |
| `plugin.displayName` | Display name in the UI | `Hello Plugin` |
| `plugin.enabled` | Enable/disable the plugin | `true` |
| `plugin.bundlePath` | Path to the JS bundle | `/main.js` |
| `resources.limits.cpu` | CPU limit | `100m` |
| `resources.limits.memory` | Memory limit | `64Mi` |
