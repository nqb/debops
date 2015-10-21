## [![DebOps project](http://debops.org/images/debops-small.png)](http://debops.org) atd

[![Travis CI](http://img.shields.io/travis/debops/ansible-atd.svg?style=flat)](http://travis-ci.org/debops/ansible-atd) [![test-suite](http://img.shields.io/badge/test--suite-ansible--atd-blue.svg?style=flat)](https://github.com/debops/test-suite/tree/master/ansible-atd/)  [![Ansible Galaxy](http://img.shields.io/badge/galaxy-debops.atd-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/5670)

The `at` and `batch` commands can be used to compliment `cron` and run
one-off tasks either at a specified time, or when the host CPU utilization is
on a low enough level.

The `debops.atd` role can be used to configure `atd` service, including
randomized load average threshold and randomized time between batch job
execution, as well as access control to the `at` and `batch` commands by
the users.

### Installation

This role requires at least Ansible `v1.9.0`. To install it, run:

    ansible-galaxy install debops.atd

### Documentation

More information about `debops.atd` can be found in the
[official debops.atd documentation](http://docs.debops.org/en/latest/ansible/roles/ansible-atd/docs/).



### Are you using this as a standalone role without DebOps?

You may need to include missing roles from the [DebOps common
playbook](https://github.com/debops/debops-playbooks/blob/master/playbooks/common.yml)
into your playbook.

[Try DebOps now](https://github.com/debops/debops) for a complete solution to run your Debian-based infrastructure.





### Authors and license

`atd` role was written by:
- Maciej Delmanowski | [e-mail](mailto:drybjed@gmail.com) | [Twitter](https://twitter.com/drybjed) | [GitHub](https://github.com/drybjed)

License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

***

This role is part of the [DebOps](http://debops.org/) project. README generated by [ansigenome](https://github.com/nickjj/ansigenome/).
