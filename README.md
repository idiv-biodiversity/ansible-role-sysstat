Ansible Role: sysstat
=====================

An Ansible role that installs [sysstat][] and configures it.

Table of Contents
-----------------

<!-- toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
  * [Top-Level Playbook](#top-level-playbook)
  * [Role Dependency](#role-dependency)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

Requirements
------------

- Ansible 2+

Role Variables
--------------

This variable controls whether to collect the performance counters with the sar service and cron jobs:

```yml
sysstat_sar_service: no
```

These variables control the collector:

```yml
sysstat_history_days: 28

sysstat_compress_after_days: 31

sysstat_sadc_options: '-S DISK'

sysstat_compression_program: bzip2
```

Dependencies
------------

None.

Example Playbook
----------------

Add to `requirements.yml`:

```yml
---

- src: idiv-biodiversity.sysstat

...
```

Download:

```console
$ ansible-galaxy install -r requirements.yml
```

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: head server
  hosts: head

  roles:
    - role: idiv-biodiversity.sysstat
      tags:
        - sysstat

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv-biodiversity.sysstat
    tags:
      - sysstat

...
```

License
-------

MIT

Author Information
------------------

This role was created in 2018 by [Christian Krause][author] aka [wookietreiber at GitHub][wookietreiber], HPC cluster systems administrator at the [German Centre for Integrative Biodiversity Research (iDiv)][idiv].


[author]: https://www.idiv.de/en/groups_and_people/employees/details/61.html
[idiv]: https://www.idiv.de/
[wookietreiber]: https://github.com/wookietreiber
[sysstat]: http://sebastien.godard.pagesperso-orange.fr/
