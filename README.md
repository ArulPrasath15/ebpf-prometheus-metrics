
# eBPF Syscall Tracer

This project uses eBPF with BCC (BPF Compiler Collection) to trace specific Linux syscalls: `clone` (for process creation) and `openat2` (for file access). It captures key runtime information including process IDs, command names, file names, and timestamps.

## 🧠 What it Does

- Tracks new process creation via `sys_clone`
- Monitors file access using `do_sys_openat2`
- Emits structured event data using BPF perf buffers

## 📁 Files

- `ebpf-probe.c`: Contains eBPF programs that hook into kernel syscalls
- `ebpf-runner.py`: Userspace Python script to load and interact with the eBPF programs using BCC

## 🛠️ Requirements

- Linux Kernel 4.1+
- Python 3.x
- BCC installed

Install BCC on Ubuntu:

```bash
sudo apt-get install bpfcc-tools linux-headers-$(uname -r) python3-bcc
