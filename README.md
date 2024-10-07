### Routine automation

![Example](/example.png)

### Reset to Factory Settings

According to the Helper Script guides and Creality's recommendations, it's strongly advised to perform a factory reset before each firmware upgrade.

```bash
ansible-playbook -i ./inventory/k1.ini playbooks/factory-reset.yaml
```

### Perform a post-install setup

Use a password for the first run since no SSH keys exist yet.

```bash
ansible-playbook -i ./inventory/k1.ini playbooks/postinstall.yaml --ask-pass
```

This will effectively copy SSH public key to the hosts and also set up a proper time according to the `timezone` variable.

### Upgrade Firmware OTA

Currently, this needs to be done manually. It would be ideal to find a way to trigger it programmatically in the future.

### Install Helper Script

```bash
ansible-playbook -i ./inventory/k1.ini playbooks/install-helper-script.yaml
```

### Git Backup Plugin

> [!WARNING]
> Make sure to clear the repo history before installing.

1. Create cr-{ansible_hostname} repos for each printer
2. Create a Fine-grained Personal Access Token allowing access to these repos
3. Use it during installation

### Troubleshooting

1. `-sk` keys are not supported by `dropbear`. Use regular ECDSA keys instead.
