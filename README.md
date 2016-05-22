Home Assistant
==============

This role deploys [Home Assistant](https://home-assistant.io/) to a remote systems.

Requirements
------------

One requirement is to have a system with a configured instance of Ansible. This means that you have an inventory and access to the remost system via SSH with keys.

1. Add the remote system to your Ansible's `hosts` (`/etc/ansible/hosts`) file to the group `[home-assistant}`.
2. For every system you want to manage, you need to have the master's SSH key in the *authorized_keys* file of the managed/remote system.

From the management system for the user **root**:

```
$ sudo ssh-copy-id -i /home/[your local user]/.ssh/id_rsa.pub root@[IP address of remote system]
```

3. Perform a first check if Ansible works:

```bash
ansible home-assistant -m ping
192.168.1.2 | success >> {
    "changed": false,
    "ping": "pong"
}
```

For further details about the setup of Ansible, check their [documentation](http://docs.ansible.com/ansible/).

Role Variables
--------------

- **ha_venv**: The location of the virtual environment. Defaults to `/opt/home-assistant`
- **ha_user**: The user for Home Assistant. Defaults to `ha`.
- **ha_port**: The default port which is 8123. If you change that your will need to modify the `configuration.yml` file of Home Assistant.
- **pkgs**: List of packages to install on the remote system.


Dependencies
------------

There are no dependencies for this role.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```bash
- hosts: home-assistant
  roles:
     - home-assistant.home-assistant-ansible
```

Warning
-------

**Think first** before you implement stuff from this repository. Consider the playbooks in this repository as non-generic. They were made especially for the deployment of Home Assistant.

License
-------

MIT

Author Information
------------------

[Fabian Affolter](https://github.com/fabaff). If you are too young to know what e-mail is, use [@fabaff](https://twitter.com/fabaff) ;-).

