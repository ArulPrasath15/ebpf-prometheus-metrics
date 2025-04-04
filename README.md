# eBPF Syscall Tracer with Prometheus Exporter

This project uses eBPF and BCC (BPF Compiler Collection) to trace specific Linux syscalls: `clone` (process creation) and `openat2` (file access). It captures runtime metadata and exposes event counts as Prometheus metrics via an HTTP server.

## 🧠 Features

- ✅ Tracks new processes via `sys_clone`
- ✅ Monitors file access using `do_sys_openat2`
- ✅ Exports metrics in Prometheus format
- ✅ Displays real-time syscall events in terminal

## 📁 Files

- `ebpf-probe.c`: eBPF program hooked into kernel syscalls
- `ebpf-runner.py`: Python script that:
  - Loads and attaches the eBPF probes
  - Parses and prints events
  - Exposes Prometheus metrics using `prometheus_client`

## 📊 Prometheus Metrics

The following metrics are exposed on port `3000` by default:

- `syscall_clone_total`: Total number of `clone` events observed
- `syscall_open_total`: Total number of `openat2` events observed


## 🛠️ Requirements

- Linux Kernel 4.1+
- Python 3.x
- BCC installed
- Prometheus client for Python

Install dependencies:

```bash
sudo apt-get install bpfcc-tools linux-headers-$(uname -r) python3-bcc
pip install prometheus_client
