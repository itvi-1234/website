---
sidebar_position: 1
title: Overview
---

# Headlamp Kmesh Plugin

The **Kmesh Plugin for Headlamp** brings native Kmesh eBPF service mesh visibility directly into the [Headlamp](https://headlamp.dev/) Kubernetes dashboard. It is the first public release (`kmesh-0.1.0-alpha`) of the plugin, published in the [headlamp-k8s/plugins](https://github.com/headlamp-k8s/plugins/releases/tag/kmesh-0.1.0-alpha) repository.

Kmesh is a high-performance, sidecar-free Layer-4/Layer-7 service mesh data plane built on eBPF. It intercepts traffic at the kernel socket layer via `sockops` and `tc` BPF hooks, without requiring sidecar containers. Headlamp is an open-source, extensible Kubernetes dashboard with a plugin architecture that lets projects like Kmesh add their own sidebar navigation, routes, resource models, and views.

<!-- TODO: add demo video here -->

## Core Capabilities

- **Waypoint Management** — Discovers and displays Kubernetes Gateway resources filtered by `gatewayClassName: kmesh-waypoint`, presenting searchable lists with status badges and enrollment indicators.
- **Daemon Health Dashboard** — Monitors `kmesh-daemon` pod readiness across all nodes, showing total vs. ready pod counts to help identify scheduling or attachment failures.
- **xDS Configuration Viewer** — Proxies requests into running daemon pods to fetch and render live ADS dumps, displaying Clusters, Listeners, and Routes in searchable tabs.
- **eBPF Telemetry Panel** — Surfaces BPF map metrics, TCP latency measurements, and packet counters without deploying additional exporters.
- **Authorization Policy Viewer** — Renders L4 authorization rules as human-readable tables mapping source workloads, destinations, and port actions.
- **eBPF Map Viewer** — For dual-engine deployments, provides tabbed access to kernel BPF state including Backends, Frontends, Services, Endpoints, and Workload Policies.
- **KmeshNodeInfo IPsec Visualization** — Displays per-node IPsec security state and daemon synchronization status through list and detail views.
- **Enrollment Indicators** — Visual badges on namespaces and waypoints show mesh membership at a glance.

<!-- TODO: add screenshots for each capability above -->

## Requirements

- Headlamp Desktop or an in-cluster Headlamp installation
- Node.js v20.11.1 or later (for building from source)
- A Kubernetes cluster reachable from Headlamp
- Kmesh installed in kernel-native or dual-engine mode
- Linux kernel 5.10+ with eBPF support
- Kubernetes permissions for `get`, `list`, and `watch` on Kmesh resources

## Development Details

The plugin implements extension APIs from `@kinvolk/headlamp-plugin` for route registration, sidebar entries, and detail view sections. All daemon communication is securely proxied through the Headlamp backend, avoiding direct browser-to-pod access. The project uses Vitest for unit testing and follows standard Headlamp packaging conventions.

## Feedback & Support

- **Bug Reports** — Open an issue on the [headlamp-k8s/plugins](https://github.com/headlamp-k8s/plugins) repository.
- **Feature Requests** — Start a discussion thread on the repository.
- **Contributions** — Pull requests are welcome; see the repository's contribution guidelines.

Released under the Apache 2.0 License.
