# Ansible

## Lab 5

- output of command ` ansible-playbook playbooks/dev/main.yml --diff`

```yaml

PLAY [Deploy Docker] ***********************************************************

TASK [Gathering Facts] *********************************************************
ok: [vm]

TASK [docker : include_tasks] **************************************************
included: /Users/vakhalilov/devopslabs/core-course-labs/ansible/roles/docker/tasks/install_pip.yml for vm

TASK [docker : Install pip] ****************************************************
ok: [vm]

TASK [docker : include_tasks] **************************************************
included: /Users/vakhalilov/devopslabs/core-course-labs/ansible/roles/docker/tasks/install_docker.yml for vm

TASK [docker : Update apt cache] ***********************************************
changed: [vm]

TASK [docker : Install Docker dependencies] ************************************
ok: [vm]

TASK [docker : Add Docker apt key] *********************************************
ok: [vm]

TASK [docker : Add Docker repository] ******************************************
ok: [vm]

TASK [docker : Install Docker] *************************************************
ok: [vm]

TASK [docker : include_tasks] **************************************************
included: /Users/vakhalilov/devopslabs/core-course-labs/ansible/roles/docker/tasks/install_compose.yml for vm

TASK [docker : Install Docker Compose] *****************************************
ok: [vm]

PLAY RECAP *********************************************************************
vm                         : ok=11   changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   


```

- output of command ` ansible-inventory -i inventory/default_yc_vm.yaml --list`

```yaml
{
    "_meta": {
        "hostvars": {
            "vm": {
                "ansible_become": true,
                "ansible_host": "51.250.71.117",
                "ansible_ssh_private_key_file": "~/.ssh/id_ed25519",
                "ansible_user": "rakavaqaflow"
            }
        }
    },
    "all": {
        "children": [
            "ungrouped",
            "yandex-cloud"
        ]
    },
    "yandex-cloud": {
        "hosts": [
            "vm"
        ]
    }
}

```

## Lab 6

### Taks 1 

output of command `ansible-playbook playbooks/dev/main.yml`:

```yml

[WARNING]: Invalid characters were found in group names but not replaced, use -vvvv to see details

PLAY [Deploy Docker image] ***************************************************************************************************

TASK [Gathering Facts] *******************************************************************************************************
ok: [vm]

TASK [web_app : Pull container] **********************************************************************************************
included: /Users/vakhalilov/devopslabs/core-course-labs/ansible/roles/web_app/tasks/pull_image.yml for vm

TASK [web_app : Pull Docker image] *******************************************************************************************
ok: [vm]

TASK [web_app : Run container] ***********************************************************************************************
included: /Users/vakhalilov/devopslabs/core-course-labs/ansible/roles/web_app/tasks/run_image.yml for vm

TASK [web_app : Run Docker container] ****************************************************************************************
changed: [vm]

PLAY RECAP *******************************************************************************************************************
vm                         : ok=5    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
```

