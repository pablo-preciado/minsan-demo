# Simple demo

This is an almost empty repo so you can just test basic git configuration with Ansible

Use ansible-vault to create secrets.yml:

```
mydemocontr: "controller22.local"
myusrcontr: "admin"
mypsscontr: "your-controller-password"
myghusr: "your-github-user"
myghtke: "your-github-token"
myrootpss: "your-root-password-for-managed-host"
```
Use the following command:
```
podman login registry.redhat.io
```

Then run the Automation Controller configuration playbook:
```
ansible-navigator run -m stdout --pae false ac-configuration.yml -e @secrets.yml --ask-vault-pass
```