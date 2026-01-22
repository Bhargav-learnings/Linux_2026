# Linux Service Management (systemd)

## What Is systemd?
systemd is the **system and service manager** used by modern Linux distributions.

- Starts system services during boot
- Manages service lifecycle
- Replaces the older init system

systemd runs as PID 1.

---

## What Is a Service?
A service is a **background process (daemon)** that runs continuously.

Examples:
- sshd
- docker
- nginx
- kubelet

---

## systemctl Command
systemctl is used to manage services.

Basic syntax:
systemctl <action> <service>

---

## Common systemctl Actions

### Start a Service
systemctl start nginx

---

### Stop a Service
systemctl stop nginx

---

### Restart a Service
systemctl restart nginx

---

### Reload a Service
systemctl reload nginx

Reload applies configuration changes without restarting the service.

---

### Check Service Status
systemctl status nginx

Shows:
- Active state
- PID
- Logs
- Errors

---

## Enable vs Disable Services

### Enable Service
systemctl enable nginx

- Starts service automatically at boot

---

### Disable Service
systemctl disable nginx

- Prevents service from starting at boot

---

### Important Difference
- stop → stops service now
- disable → affects next boot only

---

## Service States
Common service states:

- active (running)
- inactive (stopped)
- failed
- activating
- deactivating

---

## systemd Unit Files

### What Is a Unit File?
A unit file defines **how a service runs**.

Location:
- /etc/systemd/system/
- /usr/lib/systemd/system/

---

### Basic Unit File Structure
Sections:
- [Unit] → description and dependencies
- [Service] → how service runs
- [Install] → boot-time behavior

---

### Example Unit File
[Unit]
Description=My App Service

[Service]
ExecStart=/usr/bin/myapp
Restart=always

[Install]
WantedBy=multi-user.target

---

## Reload systemd After Changes
If unit file is modified:
systemctl daemon-reload

---

## Logs with journalctl

### View Logs for a Service
journalctl -u nginx

---

### Follow Logs in Real Time
journalctl -u nginx -f

---

### Logs Since Boot
journalctl -b

---

## Service Failure Troubleshooting

### Steps
1. Check service status
2. Check logs using journalctl
3. Validate configuration
4. Restart service

---

## Real Production Scenarios

### Service Not Starting on Boot
Fix:
- Ensure service is enabled
- Check unit file
- Reload systemd

---

### Service Crashing Repeatedly
Fix:
- Check logs
- Verify ExecStart path
- Check permissions

---

## Interview Summary
systemd manages system services and runs as PID 1. Services are controlled using systemctl, defined by unit files, and logged via journalctl. Enabling a service controls boot-time behavior, while starting and stopping controls runtime behavior.

---

## Key Takeaways
- systemd is the service manager
- systemctl manages services
- enable affects boot behavior
- unit files define service behavior
- journalctl is used for logs
