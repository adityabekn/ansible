# Ansible

### Initial Setup
- Enable ssh agent.
- Use `ssh-add ~/.ssh/id_rsa` for adding key to agent.
- Installing Ansible in remote computer.
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

### Running Ansible Playbook
```bash
ansible-playbook initial.yml -i inventory.yml
```