# Firecracker Python - Roadmap

This document outlines the planned features and improvements for the firecracker-python project.

## Overview

The roadmap is organized into strategic phases, each focusing on specific areas of improvement. Features are prioritized based on impact, effort, and community needs.

---

## Phase 1: Code Quality & Stability

**Goal**: Improve code quality, security, and reliability

### 1.1 Code Quality Improvements
- [ ] Fix all linting errors (ruff)
- [ ] Add mypy to dev dependencies and enable strict type checking
- [ ] Remove all bare `except:` clauses and add specific exception types
- [ ] Fix f-string without placeholders (convert to regular strings)
- [ ] Remove unused imports (`os` in config.py, `get_public_ip` in microvm.py)
- [ ] Enable pre-commit hooks for code quality

### 1.2 Enhanced Error Handling
- [ ] Create comprehensive custom exception hierarchy
- [ ] Add retry policies with exponential backoff for transient network failures
- [ ] Implement graceful degradation for non-critical features
- [ ] Add structured logging with correlation IDs for tracing
- [ ] Improve error messages with actionable guidance

### 1.3 Security Hardening
- [ ] Audit and replace `shell=True` with safer subprocess patterns
- [ ] Add comprehensive input validation for all user-facing parameters
- [ ] Implement secrets management for SSH keys and credentials
- [ ] Add sandboxing options for untrusted VMs
- [ ] Create security audit checklist and documentation
- [ ] Add permission validation before privileged operations

### 1.4 Testing Improvements
- [ ] Add integration tests for real Firecracker operations
- [ ] Add performance benchmarks (VM start time, snapshot size, I/O)
- [ ] Add chaos testing (network failures, resource exhaustion)
- [ ] Achieve >80% code coverage across all modules
- [ ] Add property-based tests for edge cases using hypothesis
- [ ] Add load testing for concurrent VM operations

---

## Phase 2: Missing Firecracker Features

**Goal**: Implement advanced Firecracker features and capabilities

### 2.1 Resource Management
- [ ] **Rate Limiting**: vCPU throttling, IOPS limits, bandwidth caps
- [ ] **Balloon Device**: Memory ballooning for overcommitment scenarios
- [ ] **CPU Templates**: Pinning to physical cores, CPU affinity configuration
- [ ] **Resource Quotas**: Per-VM and global resource limits
- [ ] **CPU C-States**: Power management and CPU state configuration
- [ ] **Intel TDX/AMD SEV**: Confidential computing support

### 2.2 Storage & Filesystems
- [ ] **Virtio-fs**: Shared directory between host and guest
- [ ] **Snapshot Compression**: Compress snapshots to save disk space
- [ ] **Incremental Snapshots**: Only save changed memory/pages
- [ ] **Multiple Block Devices**: Support additional drives beyond rootfs
- [ ] **Read-only Rootfs**: Immutable root filesystem option
- [ ] **Block Device I/O Throttling**: Per-device I/O limits

### 2.3 Networking
- [ ] **CNI Support**: Use CNI plugins for advanced networking
- [ ] **IPv6 Support**: Full dual-stack networking configuration
- [ ] **Network Bandwidth Shaping**: QoS for network interfaces
- [ ] **MAC Address Spoofing**: Allow custom MAC addresses
- [ ] **Firewall Rules**: Per-VM firewall policies and rules
- [ ] **Multiple Network Interfaces**: Support multiple NICs per VM
- [ ] **Network Isolation**: User-space networking options

### 2.4 Advanced VM Features
- [ ] **User-data with cloud-init**: Full cloud-init configuration support
- [ ] **Enhanced Vsock**: Bi-directional vsock communication API
- [ ] **Virtio-rng**: Hardware random number generator device
- [ ] **Watchdog**: Hardware watchdog timer support
- [ ] **Serial Console**: Enhanced console access with logging
- [ ] **Machine Configuration**: Advanced boot parameters and machine types

---

## Phase 3: Architecture Improvements

**Goal**: Modernize architecture for better performance and scalability

### 3.1 Async Architecture
- [ ] Add async/await support for concurrent operations
- [ ] Implement connection pooling for API calls
- [ ] Async VM creation and management methods
- [ ] Async event-driven model for VM state changes
- [ ] Support for asyncio and trio runtimes

### 3.2 Metrics & Monitoring
- [ ] **Prometheus Metrics**: Export VM metrics (CPU, memory, I/O, network)
- [ ] **Health Checks**: Periodic health status monitoring
- [ ] **Performance Profiling**: Built-in profiling tools and utilities
- [ ] **Resource Usage Tracking**: Per-VM resource consumption
- [ ] **Alerting**: Configurable alerts for resource thresholds
- [ ] **Metrics Export**: Support for multiple metric formats (Prometheus, OpenTelemetry)

### 3.3 State Management
- [ ] **VM Templates**: Pre-configured VM templates library
- [ ] **Configuration Drift Detection**: Detect and report config changes
- [ ] **State Machine**: Explicit VM lifecycle state management
- [ ] **Rollback Support**: Rollback to previous snapshots
- [ ] **Event Sourcing**: Audit trail of VM operations
- [ ] **State Persistence**: Reliable state storage across restarts

---

## Phase 4: Developer Experience

**Goal**: Improve usability and developer productivity

### 4.1 Enhanced CLI
- [ ] **Interactive CLI**: User-friendly command-line tool with prompts
- [ ] **Tab Completion**: Auto-complete for commands and parameters
- [ ] **Progress Bars**: Visual feedback for long operations
- [ ] **Rich Output**: Colorized, structured output tables
- [ ] **Configuration Files**: Support for config files (~/.firecracker/config)
- [ ] **Shell Integration**: Shell completion scripts

### 4.2 Documentation
- [ ] **Advanced Topics**: Deep-dive articles for complex features
- [ ] **Troubleshooting Guide**: Common issues and solutions
- [ ] **Security Best Practices**: Security hardening guide
- [ ] **Performance Tuning**: Optimization techniques and tips
- [ ] **Migration Guide**: Upgrading between versions
- [ ] **API Examples**: More use cases and patterns
- [ ] **Video Tutorials**: Screen casts for common workflows
- [ ] **Architecture Diagrams**: Visual documentation of components

### 4.3 Developer Tools
- [ ] **Debug Mode**: Verbose debugging with breakpoints
- [ ] **Enhanced VM Inspection**: Rich inspection tools with JSON output
- [ ] **Log Analysis**: Automatic log parsing and error highlighting
- [ ] **Configuration Validation**: Pre-flight config checks
- [ ] **Dry Run Mode**: Preview changes without execution
- [ ] **Developer Sandbox**: Isolated testing environment
- [ ] **IDE Integration**: VS Code/PyCharm extensions

---

## Phase 5: Docker-like API

**Goal**: Provide familiar container-like interface

### 5.1 Container-like Interface
- [ ] **CLI Commands**: `firecracker run`, `firecracker ps`, `firecracker rm`
- [ ] **Compose Files**: Multi-VM orchestration (docker-compose.yml format)
- [ ] **Build Context**: Build rootfs from Dockerfiles
- [ ] **Registry Support**: Pull images from container registries
- [ ] **Multi-stage Builds**: Complex build pipelines
- [ ] **Image Management**: `firecracker images` command

### 5.2 Lifecycle Management
- [ ] **Auto-restart Policies**: Restart on failure with backoff
- [ ] **Graceful Shutdown**: Handle SIGTERM/SIGINT properly
- [ ] **Dependency Management**: Start/stop VMs in dependency order
- [ ] **Health Checks**: Periodic health status with restart policies
- [ ] **Signal Handling**: Forward signals to guest processes
- [ ] **Orchestration**: Service discovery and load balancing

### 5.3 Networking & Volumes
- [ ] **Volume Mounts**: Host directory mounting (like Docker volumes)
- [ ] **Network Modes**: Bridge, host, none, custom networks
- [ ] **Port Mapping**: Simplified port forwarding syntax
- [ ] **Environment Variables**: Pass env vars to guest
- [ ] **Entrypoint/Cmd**: Configure startup commands

---

## Phase 6: Cloud Integration

**Goal**: Enable cloud-native deployment and scaling

### 6.1 Cloud Platform Support
- [ ] **AWS Integration**: Launch on EC2 with Firecracker
- [ ] **Kubernetes Operator**: Manage Firecracker VMs in K8s
- [ ] **Multi-node**: Distributed VM management
- [ ] **Scaling**: Auto-scaling based on metrics
- [ ] **Cloud-native Storage**: Integration with cloud block storage
- [ ] **Service Mesh**: Integration with Istio/Linkerd

### 6.2 Advanced Features
- [ ] **Live Migration**: Migrate running VMs between hosts
- [ ] **Checkpointing**: Advanced checkpoint/restore capabilities
- [ ] **Network Mesh**: Service discovery and mesh networking
- [ ] **Secrets Management**: Integration with secret stores (Vault, AWS Secrets)
- [ ] **Observability**: Distributed tracing integration
- [ ] **Multi-cloud**: Support multiple cloud providers

---

## Priority Matrix

| Feature | Impact | Effort | Status |
|---------|--------|---------|--------|
| Fix linting errors | High | Low | 🔴 Blocked |
| Add integration tests | High | Medium | 🟡 Planned |
| CNI support | High | High | 🟡 Planned |
| User-data with cloud-init | High | Medium | 🟡 Planned |
| Security hardening | High | Medium | 🟡 Planned |
| Prometheus metrics | High | Medium | 🔵 Future |
| Virtio-fs | Medium | High | 🔵 Future |
| Async architecture | Medium | High | 🔵 Future |
| Docker-like CLI | Medium | High | 🔵 Future |
| Kubernetes Operator | Medium | Very High | 🔴 Blocked |
| Live Migration | Medium | Very High | 🔴 Blocked |

**Legend:**
- 🔴 Blocked - Dependent on other features
- 🟡 Planned - Next phase priorities
- 🔵 Future - Long-term goals

---

## Contributing

We welcome contributions! If you're interested in working on any of these features:

1. Check the issues page for open tickets
2. Join our discussions for planning
3. Submit a PR with your changes
4. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines

---

## Related Documents

- [TODO.md](TODO.md) - Specific task list
- [AGENTS.md](AGENTS.md) - Development guidelines
- [docs/index.md](docs/index.md) - User documentation
