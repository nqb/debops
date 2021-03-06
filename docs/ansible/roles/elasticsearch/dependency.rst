.. Copyright (C) 2014-2016 Nick Janetakis <nick.janetakis@gmail.com>
.. Copyright (C) 2014-2017 Maciej Delmanowski <drybjed@gmail.com>
.. Copyright (C) 2016      Reto Gantenbein <reto.gantenbein@linuxmonk.ch>
.. Copyright (C) 2014-2017 DebOps <https://debops.org/>
.. SPDX-License-Identifier: GPL-3.0-only

.. _elasticsearch__ref_dependency:

Usage as a role dependency
==========================

The ``debops.elasticsearch`` role can be used as a dependency by other Ansible
roles to manage Elasticsearch main configuration file idempotently.
Configuration options from multiple roles can be merged together and included
in the configuration file, or removed conditionally.

.. only:: html

   .. contents::
      :local:


Dependent role variables
------------------------

The role exposes three default variables that can be used by other Ansible
roles as dependent variables:

:envvar:`elasticsearch__dependent_role`
  Required. Name of the role that uses the ``debops.elasticsearch`` as
  a dependency. This will be used to store the configuration in its own YAML
  dictionary. The selected name shouldn't be changed, otherwise configuration
  will be desynchronized.

:envvar:`elasticsearch__dependent_configuration`
  Required. List of the Elasticsearch configuration options defined in the same
  format as the main configuration. See :ref:`elasticsearch__ref_configuration`
  for more details.

:envvar:`elasticsearch__dependent_state`
  Optional. If not specified or ``present``, the configuration will be included
  in the :file:`/etc/elasticsearch/elasticsearch.yml` configuration file and
  stored as Ansible local fact. If ``absent``, the configuration will be
  removed from the generated configuration file.


Dependent configuration storage and retrieval
---------------------------------------------

The dependent configuration from other roles is stored in the :file:`secret/`
directory on the Ansible Controller (see :ref:`debops.secret` for more details) in
a JSON file, with each role configuration in a separate dictionary. The
``debops.elasticsearch`` reads this file when Ansible local facts indicate that
the Elasticsearch service is installed, otherwise a new empty file is created.
This ensures that the stale configuration is not present on a new or
re-installed host.

The YAML dictionaries from different roles are be merged with the main
configuration in the :envvar:`elasticsearch__combined_configuration` variable
that is used to generate the final configuration. The merge order of the
different ``elasticsearch__*_configuration`` variables allows to further affect
the dependent configuration through Ansible inventory if necessary, therefore
the Ansible roles that use this method don't need to provide additional
variables for this purpose themselves.


Example role variables
----------------------

This file shows an example set of default variables included in a role that
uses the ``debops.elasticsearch`` role as a dependency:

.. literalinclude:: examples/application-defaults.yml
   :language: yaml
   :lines: 1,7-

Example role playbook
---------------------

This file shows an example playbook for a role that uses the
``debops.elasticsearch`` role as a dependency:

.. literalinclude:: examples/application-playbook.yml
   :language: yaml
   :lines: 1,7-
