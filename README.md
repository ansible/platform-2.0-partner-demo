# demo-ee
Creating an EE with your collection on top of Ansible provided ones

### Prerequisites
```
# pip  install ansible-builder
# Podman or Docker installed on the build system
```

## Edit the requirements.yml file to add your collection present on Ansible Automation Hub
**Example**
```
---
collections:
  - name: vyos.vyos
```
## Edit the ansible.cfg file to add your Ansible Automation Hub Token
Scroll down to the botton of the file provided and edit the `token` key, to add the Offline Token from [Ansible Automation Hub](https://cloud.redhat.com/ansible/automation-hub/token). Load and copy the token and edit the `ansible.cfg` accordingly

> **_NOTE:_** In order to login to registry.redhat.io, run the `podman login registry.redhat.io` command with your registry.redhat.io credentials
## Run the following command in the repository after addition to create your own Execution Environment
```
ansible-builder build -v3 -c . -t <container image name>
```
Change the `<container image name>` in above command to the name you want to give to your execution environment
> **_NOTE:_** Podman is the default container-runtime, add `--container-runtime docker` to the above command if you want to use docker as the container-runtime
