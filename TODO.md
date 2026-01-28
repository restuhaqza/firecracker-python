# Firecracker Python - To Do

This document tracks specific tasks and improvements for the firecracker-python project. Tasks are organized by phase and priority.

---

## Phase 1: Code Quality & Stability

### High Priority
- [ ] Fix ruff linting errors:
  - [ ] Remove unused import `os` in `config.py`
  - [ ] Remove unused import `get_public_ip` in `microvm.py`
  - [ ] Fix bare `except:` clauses (lines 900, 906 in `microvm.py`)
  - [ ] Fix f-string without placeholders (line 894 in `microvm.py`)
- [ ] Add mypy to dependencies in `pyproject.toml`
- [ ] Enable strict type checking with mypy
- [ ] Add mypy to CI pipeline (`make ci`)
- [ ] Fix type errors reported by mypy
- [ ] Add pre-commit hooks for linting and formatting
- [ ] Replace bare `except:` with specific exception types throughout codebase
- [ ] Audit and replace `shell=True` with safer subprocess patterns
- [ ] Add input validation for all user-facing parameters
- [ ] Add permission validation before privileged operations
- [ ] Create security audit checklist
- [ ] Document security best practices

### Medium Priority
- [ ] Create comprehensive custom exception hierarchy
- [ ] Add retry policies with exponential backoff
- [ ] Implement graceful degradation for non-critical features
- [ ] Add structured logging with correlation IDs
- [ ] Improve error messages with actionable guidance
- [ ] Implement secrets management for SSH keys
- [ ] Add sandboxing options for untrusted VMs
- [ ] Add property-based tests using hypothesis
- [ ] Add chaos testing utilities
- [ ] Add performance benchmarking suite

### Low Priority
- [ ] Enable pre-commit hooks for code quality
- [ ] Add code coverage badge to README
- [ ] Add automated dependency scanning (safety, bandit)
- [ ] Add security scanning in CI pipeline

---

## Phase 2: Missing Firecracker Features

### High Priority
- [ ] **User-data with cloud-init**: Full cloud-init configuration support
  - [ ] Support for `#cloud-config` YAML format
  - [ ] Support for MIME multi-part archives
  - [ ] Add user-data validation
  - [ ] Add examples in documentation
- [ ] **CNI Support**: Use CNI plugins for networking
  - [ ] Design CNI integration architecture
  - [ ] Implement CNI plugin loader
  - [ ] Add network configuration file support
  - [ ] Test with popular CNI plugins (bridge, macvlan)
- [ ] **Enhanced Vsock**: Bi-directional vsock communication API
  - [ ] Implement vsock connection pool
  - [ ] Add async vsock support
  - [ ] Create vsock examples and tutorials

### Medium Priority
- [ ] **Virtio-fs**: Shared directory between host and guest
  - [ ] Add virtio-fs mount configuration
  - [ ] Implement directory sharing setup
  - [ ] Add permission management
- [ ] **Multiple Block Devices**: Support additional drives beyond rootfs
  - [ ] Update API to support multiple drives
  - [ ] Add drive configuration validation
  - [ ] Update documentation
- [ ] **CPU Templates**: Pinning to physical cores
  - [ ] Add CPU affinity configuration
  - [ ] Support CPU c-states configuration
  - [ ] Add NUMA awareness
- [ ] **Balloon Device**: Memory ballooning
  - [ ] Add balloon device configuration
  - [ ] Implement memory statistics API
  - [ ] Add examples of memory overcommitment
- [ ] **Snapshot Compression**: Compress snapshots to save space
  - [ ] Add compression options (gzip, zstd)
  - [ ] Implement automatic cleanup of old snapshots
  - [ ] Add snapshot size reporting
- [ ] **Incremental Snapshots**: Only save changed memory/pages
  - [ ] Implement differential snapshot logic
  - [ ] Add snapshot layer management
  - [ ] Optimize restore performance
- [ ] **IPv6 Support**: Full dual-stack networking
  - [ ] Add IPv6 address assignment
  - [ ] Update nftables rules for IPv6
  - [ ] Add IPv6 validation
- [ ] **Network Bandwidth Shaping**: QoS for network interfaces
  - [ ] Add bandwidth limit configuration
  - [ ] Implement traffic shaping
  - [ ] Add QoS monitoring
- [ ] **Firewall Rules**: Per-VM firewall policies
  - [ ] Add firewall rule configuration
  - [ ] Implement rule management API
  - [ ] Add firewall rule validation

### Low Priority
- [ ] **Rate Limiting**: vCPU throttling, IOPS limits
- [ ] **Resource Quotas**: Per-VM and global limits
- [ ] **MAC Address Spoofing**: Allow custom MAC addresses
- [ ] **Virtio-rng**: Hardware random number generator
- [ ] **Watchdog**: Hardware watchdog timer
- [ ] **Serial Console**: Enhanced console access
- [ ] **Intel TDX/AMD SEV**: Confidential computing support
- [ ] **Read-only Rootfs**: Immutable root filesystem
- [ ] **Block Device I/O Throttling**: Per-device I/O limits

---

## Phase 3: Architecture Improvements

### High Priority
- [ ] **Async API**: Add async/await support
  - [ ] Create async API client
  - [ ] Implement connection pooling
  - [ ] Add async VM lifecycle methods
  - [ ] Provide both sync and async APIs
- [ ] **Prometheus Metrics**: Export VM metrics
  - [ ] Add metrics endpoint
  - [ ] Export CPU, memory, I/O, network metrics
  - [ ] Add metric labels (vm_id, etc.)
  - [ ] Create Prometheus exporter
- [ ] **Health Checks**: Periodic health monitoring
  - [ ] Implement health check endpoints
  - [ ] Add configurable health check intervals
  - [ ] Support multiple health check types
  - [ ] Add health status reporting

### Medium Priority
- [ ] **Event-driven Model**: Async VM state changes
  - [ ] Implement event bus for state changes
  - [ ] Add webhook support for events
  - [ ] Create event filtering API
- [ ] **Performance Profiling**: Built-in profiling tools
  - [ ] Add profiling decorators
  - [ ] Export profiling data
  - [ ] Add performance reports
- [ ] **Resource Usage Tracking**: Per-VM consumption
  - [ ] Track CPU usage over time
  - [ ] Track memory usage over time
  - [ ] Track I/O and network usage
  - [ ] Add usage reporting API
- [ ] **Alerting**: Configurable alerts for thresholds
  - [ ] Add alert rules configuration
  - [ ] Implement alert evaluation
  - [ ] Support multiple alert channels
- [ ] **VM Templates**: Pre-configured templates
  - [ ] Create template library
  - [ ] Add template validation
  - [ ] Support custom templates
  - [ ] Add template marketplace

### Low Priority
- [ ] **Metrics Export**: Support multiple formats (OpenTelemetry)
- [ ] **Configuration Drift Detection**: Detect config changes
- [ ] **State Machine**: Explicit VM lifecycle states
- [ ] **Rollback Support**: Rollback to snapshots
- [ ] **Event Sourcing**: Audit trail of operations
- [ ] **State Persistence**: Reliable storage across restarts
- [ ] Support for asyncio and trio runtimes

---

## Phase 4: Developer Experience

### High Priority
- [ ] **Interactive CLI**: User-friendly command-line tool
  - [ ] Design CLI command structure
  - [ ] Implement `firecracker` CLI with subcommands
  - [ ] Add interactive prompts for complex operations
  - [ ] Add help system and examples
- [ ] **Configuration Files**: Support for config files
  - [ ] Add `~/.firecracker/config` support
  - [ ] Define config file format (YAML/TOML)
  - [ ] Add config validation
  - [ ] Document config options
- [ ] **Advanced Documentation**: Deep-dive articles
  - [ ] Write advanced topics guide
  - [ ] Create troubleshooting guide
  - [ ] Document security best practices
  - [ ] Write performance tuning guide
- [ ] **API Examples**: More use cases and patterns
  - [ ] Add examples for all major features
  - [ ] Create pattern library
  - [ ] Add code snippets to documentation

### Medium Priority
- [ ] **Tab Completion**: Auto-complete for commands
  - [ ] Implement bash completion
  - [ ] Implement zsh completion
  - [ ] Add fish completion
  - [ ] Document completion installation
- [ ] **Progress Bars**: Visual feedback for operations
  - [ ] Add progress bars for long operations
  - [ ] Support cancellation
  - [ ] Add time estimates
- [ ] **Rich Output**: Colorized, structured output
  - [ ] Use rich library for tables
  - [ ] Add color themes
  - [ ] Format JSON output
- [ ] **Debug Mode**: Enhanced debugging tools
  - [ ] Add verbose debugging mode
  - [ ] Implement breakpoint support
  - [ ] Add debug logging
- [ ] **VM Inspection**: Enhanced inspection tools
  - [ ] Add JSON output format
  - [ ] Add filtering options
  - [ ] Display detailed configuration
- [ ] **Log Analysis**: Automatic log parsing
  - [ ] Parse Firecracker logs
  - [ ] Highlight errors and warnings
  - [ ] Extract performance metrics
- [ ] **Configuration Validation**: Pre-flight checks
  - [ ] Validate kernel and rootfs compatibility
  - [ ] Check resource availability
  - [ ] Warn about potential issues

### Low Priority
- [ ] **Shell Integration**: Shell completion scripts
- [ ] **Migration Guide**: Upgrading between versions
- [ ] **Video Tutorials**: Screen casts for workflows
- [ ] **Architecture Diagrams**: Visual documentation
- [ ] **Dry Run Mode**: Preview changes without execution
- [ ] **Developer Sandbox**: Isolated testing environment
- [ ] **IDE Integration**: VS Code/PyCharm extensions
- [ ] **Interactive Prompts**: Enhanced user input

---

## Phase 5: Docker-like API

### High Priority
- [ ] **CLI Commands**: `firecracker run`, `firecracker ps`, `firecracker rm`
  - [ ] Implement `firecracker run` command
  - [ ] Implement `firecracker ps` command
  - [ ] Implement `firecracker rm` command
  - [ ] Implement `firecracker stop`, `firecracker start`
  - [ ] Add command help and examples
- [ ] **Compose Files**: Multi-VM orchestration
  - [ ] Define `firecracker-compose.yml` format
  - [ ] Implement compose file parser
  - [ ] Support multi-VM management
  - [ ] Add lifecycle commands (up, down, ps)
- [ ] **Port Mapping**: Simplified port forwarding
  - [ ] Add `-p` flag for port mapping
  - [ ] Support `host:guest` format
  - [ ] Support port ranges
  - [ ] Add port conflict detection

### Medium Priority
- [ ] **Build Context**: Build rootfs from Dockerfiles
  - [ ] Add Dockerfile support
  - [ ] Implement build cache
  - [ ] Support multi-stage builds
  - [ ] Add build output customization
- [ ] **Volume Mounts**: Host directory mounting
  - [ ] Add `-v` flag for volumes
  - [ ] Support read-only mounts
  - [ ] Add permission management
- [ ] **Environment Variables**: Pass env vars to guest
  - [ ] Add `-e` flag for environment variables
  - [ ] Support `.env` files
  - [ ] Document variable precedence
- [ ] **Auto-restart Policies**: Restart on failure
  - [ ] Add `--restart` flag
  - [ ] Support no, always, on-failure policies
  - [ ] Implement restart backoff
- [ ] **Graceful Shutdown**: Handle signals properly
  - [ ] Implement SIGTERM/SIGINT handlers
  - [ ] Ensure clean VM shutdown
  - [ ] Add timeout for graceful shutdown

### Low Priority
- [ ] **Registry Support**: Pull images from registries
- [ ] **Image Management**: `firecracker images` command
- [ ] **Network Modes**: Bridge, host, none networks
- [ ] **Entrypoint/Cmd**: Configure startup commands
- [ ] **Dependency Management**: Start/stop in order
- [ ] **Health Checks**: Periodic health with restart

---

## Phase 6: Cloud Integration

### High Priority
- [ ] **Kubernetes Operator**: Manage Firecracker VMs in K8s
  - [ ] Design CRD for FirecrackerVM
  - [ ] Implement operator controller
  - [ ] Add reconciliation logic
  - [ ] Create Helm charts
- [ ] **Multi-node**: Distributed VM management
  - [ ] Design distributed architecture
  - [ ] Implement node discovery
  - [ ] Add VM placement logic
  - [ ] Support VM migration

### Medium Priority
- [ ] **AWS Integration**: Launch on EC2
  - [ ] Add EC2 AMI builder
  - [ ] Implement EC2 launch wrapper
  - [ ] Add AWS IAM integration
  - [ ] Support spot instances
- [ ] **Scaling**: Auto-scaling based on metrics
  - [ ] Define scaling policies
  - [ ] Implement auto-scaler
  - [ ] Add metrics-based triggers
- [ ] **Cloud-native Storage**: Integration with cloud storage
  - [ ] Support EBS volumes
  - [ ] Add snapshot to S3
  - [ ] Implement storage lifecycle

### Low Priority
- [ ] **Live Migration**: Migrate running VMs
- [ ] **Checkpointing**: Advanced checkpoint/restore
- [ ] **Network Mesh**: Service discovery and mesh
- [ ] **Secrets Management**: Vault/AWS Secrets integration
- [ ] **Observability**: Distributed tracing
- [ ] **Multi-cloud**: Support multiple cloud providers

---

## Quick Wins (Easy Tasks)

These are low-effort tasks that provide immediate value:

- [ ] Fix type annotations for optional parameters
- [ ] Add docstrings to all public methods
- [ ] Add type hints to all function signatures
- [ ] Create CONTRIBUTING.md with contribution guidelines
- [ ] Add CHANGELOG.md for version tracking
- [ ] Set up automated release notes generation
- [ ] Add issue templates for bug reports and feature requests
- [ ] Add PR template for pull requests
- [ ] Create code of conduct
- [ ] Add GitHub Actions workflow for CI/CD
- [ ] Add release Drafter for automated changelog
- [ ] Set up Dependabot for dependency updates
- [ ] Add sponsors section to README
- [ ] Create logo and branding materials
- [ ] Add code coverage badge to README
- [ ] Add PyPI download badge to README

---

## In Progress

- None currently

---

## Completed

- None tracked in TODO.md (check git history for completed items)

---

## How to Contribute

1. **Pick a task**: Choose an item from this list that matches your skills
2. **Create an issue**: Create a GitHub issue for the task
3. **Get feedback**: Discuss implementation approach with maintainers
4. **Submit PR**: Create a pull request with your changes
5. **Update TODO**: Mark item as completed and add date

---

## Related Documents

- [ROADMAP.md](ROADMAP.md) - Strategic roadmap and phases
- [AGENTS.md](AGENTS.md) - Development guidelines
- [docs/index.md](docs/index.md) - User documentation
- [README.md](README.md) - Project overview
