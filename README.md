# vpn-kit-case

A short case study of a private production VPN infrastructure I built and operate for personal use and a small circle of trusted users.

The system provides reproducible WireGuard VPN deployment across multiple servers, with monitoring, encrypted secrets, backups, and deployment automation. The production repository remains private; this repository documents the engineering work without exposing operational secrets, live runbooks, or infrastructure history.

## What was built

- Multi-server WireGuard infrastructure using `wg-easy`.
- Automated provisioning and deployment with Ansible and GitHub Actions.
- Per-server encrypted secrets with SOPS and age.
- Separate monitoring stack with Prometheus, Grafana, Alertmanager, node-exporter, cAdvisor, and blackbox exporter.
- Notification relay through a Cloudflare Worker, delivering alerts to Telegram and email.
- Encrypted offsite backups with restic to S3-compatible storage.
- Firewall rules that account for Docker networking and restrict exporter access to the monitoring server.

## Production experience

This is not a toy example. The system has been used in production, including real operational work:

- bootstrapping fresh servers safely without storing root credentials in CI;
- migrating from single-server to multi-server VPN inventory;
- handling DNS, SSH host key, Docker, storage, and monitoring failures;
- debugging `wg-easy` v15 migration behavior and WireGuard key compatibility;
- improving deploy notifications and observability after real incidents.

## Why it matters

The project demonstrates practical infrastructure engineering: automation, secret boundaries, monitoring, incident response, backup strategy, and safe deployment workflows for a small but real production environment.
