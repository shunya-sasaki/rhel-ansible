# Red Hat Enterprise Linux Ainsible

Ansible project for the RHEL.

## Usage

### Setup remote ssh

To set up a remote server with Ansible, SSH connections are required. To enable SSH connections, create an SSH key on the remote server and register the key on your local machine where you will run Ansible.

First, run the following command in the remote server to create ssh keys.

```sh
ssh-keygen -t rsa -b 4096
```

Second, create the `~/.ssh/authorized_keys` file on the remote server and copy the content of your public key from your local machine into this file.

### Create a inventory file

First, create an inventory file that defines groups of hosts.
You can use an arbitrary file name.
The file contents are below.

```yaml
[your_group_name]
192.168.1.10
```

### Test to connect to hosts

Run the following command to list the hosts that are written in an inventory file.

```sh
ansible-inventory -i INVENTRY_FILE --list
```

```sh
ansible YOUR_GROUP -m ping -i INVENTORY_FILE
```

If the group name is `rhel` and the inventry file is `develop`,
run the following command.

```sh
ansible rhel -m ping -i develop
```

### Run the playbooks

To run Ansible, execute the following command,
replacing USER with the username of the remote hosts.

```sh
ansible-playbook -i INVENTORY_FILE root.yml --user USER
```

## License

[LICENSE](./LICENSE)

## Author

- Shunya Sasaki
  - Mail: [shunya.sasaki1120@gmail.com](mailto:shunya.sasaki1120@gmail.com)
  - X: [@ShunyaSasaki](https://x.com/ShunyaSasaki)
