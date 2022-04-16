# Ansible Demo Project

A simple project that demonstrates how Ansible works. I did not want to install ansible and python on my host machine, so
I tried to do in docker. Be aware of that because some modules in playbooks may not work (e.g. that uses systemctl, because no systemd available inside docker container)

## How to run

- Build a docker image with Ansible installed - `docker run -t eshishkin/ansible .`
- Build a docker image with ssh daemon - `docker run -t eshishkin/ssh -f Dockerfile.shh .`
- Generate a pair of private/public key and put it into `keys/master`
- Put the public key into `slaves/authorized_keys` (change permissions if needed)
- Run `compose` file - `docker-compose up -d`
- Connect to container wit Ansible - ` docker exec -it <container_id> bash` (container_id can be taken from output of `docker ps`)
- Go to `opt/ansible/playbooks/` inside the container and do anything you want with Ansible. E.g. ping all available nodes `ansible all -m ping -i inventory.yml`
