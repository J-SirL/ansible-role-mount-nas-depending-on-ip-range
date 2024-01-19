# Role: `mount_nas_depending_on_ip_range`

## Table of Contents

- [Role Name](#role-name-mount_nas_depending_on_ip_range)
- [Author](#author-johan-sörell)
- [Role Description](#role-description)
- [Features](#features)
- [Usage](#usage)
  - [Clone the Git Repository](#1-clone-the-git-repository)
  - [Include the Role in Your Ansible Playbook](#2-include-the-role-in-your-ansible-playbook)
  - [Configure Variables](#3-configure-variables)
  - [Execute the Ansible Playbook](#4-execute-the-ansible-playbook)

## Author: Johan Sörell

## Role Description

The `mount_nas_depending_on_ip_range` is an Ansible role designed to simplify the setup of a Network Attached Storage (NAS) mount script as a Systemd service triggered by network changes, with configuration depending on IP address ranges. This role automates the configuration of the NAS mount script, Systemd service, and NetworkManager dispatcher script, allowing you to mount NAS shares based on specific IP address ranges, enhancing security and flexibility.

## Features

- Uploads the NAS mount script to the specified path on the local machine.
- Creates a Systemd service file for the script, ensuring proper execution and management.
- Generates a NetworkManager dispatcher script to trigger the service when network changes occur, depending on the local IP address.
- Provides flexibility to configure various parameters, such as NAS IP, share name, mount point, mount type, and IP address ranges.

## Usage

### 1. Clone the Git Repository

Clone this Git repository to your Ansible project:

```shell
git clone https://github.com/your-username/mount_nas_depending_on_ip_range.git
```

### 2. Include the Role in Your Ansible Playbook

Include the `mount_nas_depending_on_ip_range` role in your Ansible playbook:

```yaml
---
- name: Configure NAS Mount
  hosts: localhost
  connection: local
  become: yes
  roles:
    - mount_nas_depending_on_ip_range
```

### 3. Configure Variables

Configure the desired variables in your playbook, customizing the NAS IP, share name, mount point, mount type, local network IP prefix, and other parameters as needed:

```yaml
---
# configure_nas_mount.yml
- name: Configure NAS Mount
  hosts: localhost
  connection: local
  become: yes
  roles:
    - mount_nas_depending_on_ip_range
  vars:
    nas_ip: "192.168.48.110"  # Change to the new NAS IP address
    share_name: "/BackupShare"  # Change to the new NAS share name
    mount_point: "/mnt/BackupShare/"  # Change to the new mount point
    mount_type: "nfs"  # or "cifs"
    local_network_ip_prefix: "192.168.48"  # Change to the new local network IP prefix
```

### 4. Execute the Ansible Playbook

Execute your Ansible playbook to set up the NAS mount script and related components:

```shell
ansible-playbook configure_nas_mount.yml
```

This role is suitable for users who want to automate the setup of NAS mounts on their local system while customizing the mount configuration based on specific IP address ranges. It simplifies the process of configuring and managing NAS mounts, enhancing security and flexibility in your infrastructure.

**Author Bio:**

Johan Sörell is an experienced IT professional with a passion for automation and infrastructure management. With a strong background in system administration and DevOps practices, Johan has a track record of optimizing workflows and enhancing system reliability through automation.

LinkedIn Profile: [Johan Sörell LinkedIn](https://www.linkedin.com/in/johansorell/)

Johan actively contributes to the open-source community and shares insights on technology trends through various channels. With a commitment to simplifying complex tasks, Johan's role in the development of the `mount_nas_depending_on_ip_range` reflects a dedication to making system configuration more accessible and efficient for all users. Connect with Johan on LinkedIn to stay updated on the latest advancements in IT automation and infrastructure management.
