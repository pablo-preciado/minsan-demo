# Simple demo

This is an almost empty repo so you can just test basic git configuration with Ansible

First update the inventory/hosts file with the proper IP address or FQDN.

Then use ansible-vault to create secrets.yml:

```
mydemocontr: "your-ac-fqdn-or-ip"
myusrcontr: "your-ac-username"
mypsscontr: "your-controller-password"
myghusr: "your-github-user"
myghtke: "your-github-token"
mytargetusr: "your-managed-server-username"
mytargetpss: "your-password-for-target-server"
```
Use the following command:
```
podman login registry.redhat.io
```

Then run the Automation Controller configuration playbook:
```
ansible-navigator run -m stdout --pae false ac-configuration.yml -e @secrets.yml --ask-vault-pass
```

To test Github webhooks, in your Github repo go to Settings > Webhooks > Add webhook. The paste the URL you can find in the atomation controller under "Webhook URL" in "Simple demo delete file" job template details. Select application/json as content type in Github. Last, paste the secrete you can find in "Webhook Key" in "Simple demo delete file" job template details of your controller.

Test the webhook with an empty commit:
```
git commit -m "empty-commit" --allow-empty && git push
```
---
