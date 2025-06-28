# vantage_agents Ansible Role


This role installs and configures the `vantage-agent` and `jobbergate-agent` on Linux hosts (Debian, Ubuntu, RHEL, CentOS, Rocky, Alma, etc.) using either Snap (default) or PyPI, as determined by the `install_type` variable. It sets OIDC credentials and cluster name, and ensures both agents are running.

## Requirements
- Linux host (Debian/Ubuntu or RHEL/CentOS/Rocky/Alma)
- snapd available (role will install if missing)
- Ansible 2.9+

## Role Variables
| Variable           | Description                                 | Default         |
|--------------------|---------------------------------------------|-----------------|
| oidc_client_id     | OIDC client ID for both agents              | ""              |
| oidc_client_secret | OIDC client secret for both agents          | ""              |
| cluster_name       | Cluster name for vantage-agent              | ""              |
| install_type       | Installation type: `snap` or `pypi`         | "snap"           |

## Example Playbook


```yaml
- hosts: util_node
  become: true
  vars:
    oidc_client_id: "<your-oidc-client-id>"
    oidc_client_secret: "<your-oidc-client-secret>"
    cluster_name: "<your-cluster-name>"
    install_type: "snap"   # or "pypi"
  roles:
    - role: vantage_agents
```


> **Note:**
> - Set `install_type` to `snap` (default) or `pypi` to control installation method.
> - For `snap`, the role will install snapd if missing.
> - For `pypi`, the role will install Python, create virtual environments, and deploy systemd services for both agents.

## License
Apache-2.0

## Author Information
Vantage Compute <info@vantagecompute.ai>
