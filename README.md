# lab-ansible
Configuration management for the lab servers (found automatically by AWS tags).

| Playbook | Purpose |
|---|---|
| `playbooks/site.yml` | Build every server: baseline/hardening, node_exporter, Docker, Nexus + SonarQube, Jenkins (configuration as code), nginx |
| `playbooks/patch.yml` | Rolling OS patching with pre/post checks |
| `playbooks/cleanup.yml` | Disk housekeeping |

```bash
pip install ansible-core boto3 botocore && ansible-galaxy collection install -r requirements.yml
export JENKINS_ADMIN_PASSWORD=... SONAR_DB_PASSWORD=...
ansible-inventory --graph && ansible-playbook playbooks/site.yml
```
