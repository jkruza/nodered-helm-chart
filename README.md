# nodered-helm-chart

This repository contains a Helm chart for deploying [Node-RED](https://nodered.org/) on Kubernetes. Node-RED is a flow-based development tool for visual programming, ideal for IoT and other event-driven applications.

## Features

- Easy deployment of Node-RED on Kubernetes.
- Configurable settings for Node-RED, including persistence and resource limits.
- Support for custom Node-RED flows and additional nodes.

## Prerequisites

- Kubernetes cluster (v1.20+ recommended).
- Helm 3.x installed.
- Basic knowledge of Kubernetes and Helm.

## Installation

1. Add the Helm repository (if applicable):
   ```bash
   helm repo add <repo-name> <repo-url>
   helm repo update
   ```

2. Install the chart:
   ```bash
   helm install my-nodered <repo-name>/nodered-helm-chart
   ```

   Replace `my-nodered` with your desired release name.

3. Verify the installation:
   ```bash
   kubectl get all -l app.kubernetes.io/name=nodered
   ```

## Configuration

The chart can be customized using a `values.yaml` file. Below are some common configuration options:

- `replicaCount`: Number of Node-RED replicas.
- `resources`: Resource requests and limits for the Node-RED container.
- `persistence`: Enable or disable persistent storage.

Example:
```yaml
replicaCount: 2
resources:
  limits:
    cpu: 500m
    memory: 256Mi
persistence:
  enabled: true
  size: 1Gi
```

Apply custom configurations during installation:
```bash
helm install my-nodered <repo-name>/nodered-helm-chart -f values.yaml
```

## Usage

Once deployed, access Node-RED via the service's external IP or ingress (if configured). The default credentials can be set in the `values.yaml` file.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes with clear messages.
4. Open a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.