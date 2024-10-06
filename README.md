### Reset to the factory settings

```bash
ansible-playbook -i ./inventory/k1 playbooks/factory-reset.yaml --ask-pass
```

### Upgrade firmware OTA

Manually for now

### Install Script

```bash
ansible-playbook -i ./inventory/k1 playbooks/install-helper-script.yaml --ask-pass
```
