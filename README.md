Red Hat Subscription
=========

Manage Red Hat subscritions and repositories.

Requirements
------------

Current Red Hat subscription.

Role Variables
--------------

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `rhn_username` | `{{ lookup('env', 'RHN_USERNAME') }}` | Red Hat Port username. |
| `rhn_password` | `{{ lookup('env', 'RHN_PASSWORD') }}` | Red Hat Portal password. |
| `rhsub_state` | `enable` | Whether to enable or disable a Red Hat subscription. |
| `rhsub_autosubscribe` | `True` | Whether or not to autosubscibe to available repositories. If set, will skip the task that manages individual repositories.  |
| `rhsub_repos` | `{}` | List of repositories to enable or disable. See `defaults/main.yml` for examples. |

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all

      vars:
        rhn_username: bob.smith@acme.com
        rhn_password: "{{ vault_rhn_password }}"
        rhsub_repos:
          - name: rhel-7-server-extras-rpms
            state: enable

      roles:
         - samdoran.redhat-subscription

License
-------

MIT

