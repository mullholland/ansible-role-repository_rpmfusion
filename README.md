# [repository_rpmfusion](#repository_rpmfusion)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-repository_rpmfusion/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_rpmfusion/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-repository_rpmfusion/badges/master/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-repository_rpmfusion)|[![quality](https://img.shields.io/ansible/quality/unset)](https://galaxy.ansible.com/mullholland/repository_rpmfusion)|

Install the RPM Fusion repository (free and nonfree possible)

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
repository_rpmfusion_free_enable: true
repository_rpmfusion_free:
  RedHat:
    "7":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
  CentOS:
    "7":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
  Rocky:
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
  AlmaLinux:
    "8":
      - "https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm"
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

repository_rpmfusion_nonfree_enable: true
repository_rpmfusion_nonfree:
  RedHat:
    "7":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
  CentOS:
    "7":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-7.noarch.rpm"
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
  Rocky:
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
  AlmaLinux:
    "8":
      - "https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-8.noarch.rpm"
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
```


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
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

The machine needs to be prepared in CI this is done using `molecule/default/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: mullholland.repository_codereadybuilder
      when:
        - (ansible_distribution == "RedHat" and ansible_distribution_major_version == "8") or
          (ansible_distribution == "CentOS" and ansible_distribution_major_version == "9")
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





## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

-   [centos7](https://hub.docker.com/r/mullholland/docker-molecule-centos7)
-   [centos-stream8](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream8)
-   [ubi8](https://hub.docker.com/r/mullholland/docker-molecule-ubi8)
-   [fedora34](https://hub.docker.com/r/mullholland/docker-molecule-fedora34)
-   [fedora35](https://hub.docker.com/r/mullholland/docker-molecule-fedora35)
-   [amazonlinux](https://hub.docker.com/r/mullholland/docker-molecule-amazonlinux)
-   [rockylinux8](https://hub.docker.com/r/mullholland/docker-molecule-rockylinux8)
-   [almalinux8](https://hub.docker.com/r/mullholland/docker-molecule-almalinux8)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The last 2 versions.
-   The current version.



## [Exceptions](#exceptions)

Some variations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| Ubuntu* | repo only supports RedHat/CentOS based systems |
| Debian* | repo only supports RedHat/CentOS based systems |
| centos-stream9 | Not supported ATM (https://twitter.com/rpmfusion_team/status/1467405564317769735) |


If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-repository_rpmfusion/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
