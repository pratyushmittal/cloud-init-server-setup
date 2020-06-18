# Configure servers in minutes

Use `cloud-config.yaml` to configure a virtual server in minutes.

## Using

The script installs:
- ssh keys
- timezone
- postfix for crons emails
- docker
- docker-compose
- repos directory
- webapps directory

Docker and Docker-compose are good for managing project specific dependencies. Use them.

## Setup on local machine

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Commands

```bash
# validation
python validate-yaml.py cloud-config.yaml

# testing the script locally
## https://multipass.run
## https://cloudinit.readthedocs.io/en/latest/topics/faq.html#multipass
multipass launch -n ubuntu-lts-custom --cloud-init cloud-config.yaml
# get into bash
multipass exec ubuntu-lts-custom bash
# see logs
#https://cloudinit.readthedocs.io/en/latest/topics/faq.html#where-are-the-logs
cat /run/cloud-init/result.json
# delete virtual clouds
multipass delete ubuntu-lts-custom
multipass purge
```
