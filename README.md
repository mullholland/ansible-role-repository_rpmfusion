# [Ansible role repository_rpmfusion](#repository_rpmfusion)

Install the RPM Fusion repository (free and nonfree possible)

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-repository_rpmfusion/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-repository_rpmfusion/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/repository_rpmfusion)](https://galaxy.ansible.com/mullholland/repository_rpmfusion)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-repository_rpmfusion.svg)](https://github.com/mullholland/ansible-role-repository_rpmfusion/releases/)|
## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-repository_rpmfusion/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "mullholland.repository_rpmfusion"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-repository_rpmfusion/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: mullholland.repository_powertools
      when:
        - ansible_distribution in [ "CentOS", "Rocky", "AlmaLinux" ]
        - ansible_distribution_major_version == "8"
    - role: mullholland.repository_epel
      when:
        - (ansible_distribution == "Amazon" and
          ansible_distribution_major_version == "2") or
          (ansible_distribution in [ "RedHat", "CentOS", "Rocky", "AlmaLinux" ])
```



## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-repository_rpmfusion/blob/master/defaults/main.yml):

```yaml
---
repository_rpmfusion_free_enable: true
repository_rpmfusion_free_key:
  RedHat:
    "7":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-7"
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-9"
  CentOS:
    "7":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-7"
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-9"
  Rocky:
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-9"
  AlmaLinux:
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-9"
  Amazon:
    "2":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-el-7"
  Fedora:
    "33":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"
    "34":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"
    "35":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"
    "36":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"
    "37":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"
    "38":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"
    "39":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"
    "40":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-2020"

repository_rpmfusion_free:
  RedHat:
    "7":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-9.noarch.rpm"
  CentOS:
    "7":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-9.noarch.rpm"
  Rocky:
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-9.noarch.rpm"
  AlmaLinux:
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-9.noarch.rpm"
  Amazon:
    "2":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm"
  Fedora:
    "33":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-33.noarch.rpm"
    "34":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-34.noarch.rpm"
    "35":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-35.noarch.rpm"
    "36":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-36.noarch.rpm"
    "37":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-37.noarch.rpm"
    "38":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-38.noarch.rpm"
    "39":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-39.noarch.rpm"
    "40":
      - "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-40.noarch.rpm"

repository_rpmfusion_nonfree_enable: true
repository_rpmfusion_nonfree_key:
  RedHat:
    "7":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-7"
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-9"
  CentOS:
    "7":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-7"
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-9"
  Rocky:
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-9"
  AlmaLinux:
    "8":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-8"
    "9":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-9"
  Amazon:
    "2":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-el-7"
  Fedora:
    "33":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"
    "34":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"
    "35":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"
    "36":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"
    "37":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"
    "38":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"
    "39":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"
    "40":
      - "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-fedora-2020"

repository_rpmfusion_nonfree:
  RedHat:
    "7":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-9.noarch.rpm"
  CentOS:
    "7":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-9.noarch.rpm"
  Rocky:
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-9.noarch.rpm"
  AlmaLinux:
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
    "9":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-9.noarch.rpm"
  Amazon:
    "2":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-7.noarch.rpm"
  Fedora:
    "33":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-33.noarch.rpm"
    "34":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-34.noarch.rpm"
    "35":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-35.noarch.rpm"
    "36":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-36.noarch.rpm"
    "37":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-37.noarch.rpm"
    "38":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-38.noarch.rpm"
    "39":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-39.noarch.rpm"
    "40":
      - "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-40.noarch.rpm"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-repository_rpmfusion/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[mullholland.repository_powertools](https://galaxy.ansible.com/mullholland/repository_powertools)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-repository_powertools/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_powertools/actions)|[![Build Status GitLab](https://gitlab.com/opensourceunicorn/ansible-role-repository_powertools/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-repository_powertools)|
|[mullholland.repository_epel](https://galaxy.ansible.com/mullholland/repository_epel)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-repository_epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_epel/actions)|[![Build Status GitLab](https://gitlab.com/opensourceunicorn/ansible-role-repository_epel/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-repository_epel)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-repository_rpmfusion/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/mullholland/enterpriselinux)|all|
|[Amazon](https://hub.docker.com/r/mullholland/amazonlinux)|Candidate|
|[Fedora](https://hub.docker.com/r/mullholland/fedora/)|38, 39|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-repository_rpmfusion/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-repository_rpmfusion/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
