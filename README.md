This repository accompanies <https://stackoverflow.com/q/75262503/147356>.

I'm using a container as a target for the tests:

```
docker run --rm -d --privileged --name node0 ubuntu:22.04 sleep inf
docker exec node0 apt update
docker exec node0 apt -y install tzdata python3 sudo
```

Once the container is ready:

```
ansible-playbook playbook.yaml
```

The output looks like:

```
PLAY [all] **********************************************************************************************

TASK [Set hostname] *************************************************************************************
changed: [node0]

TASK [Set timezone] *************************************************************************************
changed: [node0]

TASK [Update all packages] ******************************************************************************
changed: [node0]

PLAY RECAP **********************************************************************************************
node0                      : ok=3    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
