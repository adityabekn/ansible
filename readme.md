# Ansible

### Prerequisite
- Enable ssh agent.
- Use `ssh-add ~/.ssh/id_rsa` for adding key to agent.

### Installing
```bash
UBUNTU_CODENAME=jammy
```

```bash
wget -O- "https://keyserver.ubuntu.com/pks/lookup?fingerprint=on&op=get&search=0x6125E2A8C77F2818FB7BD15B93C4A3FD7BB9C367" | sudo gpg --dearmour -o /usr/share/keyrings/ansible-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/ansible-archive-keyring.gpg] http://ppa.launchpad.net/ansible/ansible/ubuntu $UBUNTU_CODENAME main" | sudo tee /etc/apt/sources.list.d/ansible.list
```

```bash
sudo apt update && sudo apt install ansible
```

- Check Ansible version `ansible --version`.
- Try ping with ansible `ansible -i inventory.yml -m ping`.
- add `--ask-pass` for password ssh
- add `--ask-become-pass` for privilege password
- add `ansible_ssh_private_key_file=./files/homelab` for private key ssh in `inventory.yml`

### Running Ansible Playbook
Example running playbook:

```bash
ansible-playbook initial.yml -i inventory.yml
```

`playbook-user.yml` for creating user if only root available.

`paybook-initial.yml` for config intial setup

`playbook-post-install.yml` for install the addon after intial setup