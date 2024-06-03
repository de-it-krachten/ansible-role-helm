[![CI](https://github.com/de-it-krachten/ansible-role-helm/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-helm/actions?query=workflow%3ACI)


# ansible-role-helm

Installs helm onto a variety of platforms<br>
https://helm.sh<br>
https://github.com/helm/helm<br>



## Dependencies

#### Roles
None

#### Collections
- kubernetes.core

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 39
- Fedora 40

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Github CLI - API
helm_api: https://api.github.com/repos/helm/helm

# Github CLI - repo
helm_repo: https://github.com/helm/helm

# Helm archive
helm_archive_url: https://get.helm.sh/{{ helm_file }}

# Lookup table for architecture
helm:
  architecture:
    x86_64: amd64
    i386: i386
    armv6l: arm
    armv7l: arm
    aarch64: arm64
  system:
    Linux: linux
    Darwin: darwin

# Version of the CLI to install
helm_version: latest

# Location/ownership/permissions of the binary
helm_path: /usr/local/bin/helm
helm_owner: root
helm_group: root
helm_mode: '0755'

helm_plugins:
  - path: https://github.com/databus23/helm-diff
    state: present
#   - name: diff
#     state: absent
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'helm'
  hosts: all
  become: 'yes'
  tasks:
    - name: Include role 'helm'
      ansible.builtin.include_role:
        name: helm
</pre></code>
